## 목차
- [Number Theory II](#number-theory-ii)
  - [Encryption Basics (암호화 기초)](#encryption-basics-암호화-기초)
  - [Turing’s Code v1 (단순 곱셈 방식)](#turings-code-v1-단순-곱셈-방식)
  - [Turing’s Code v2 (모듈러 곱셈)](#turings-code-v2-모듈러-곱셈)
  - [Modular Arithmetic Essentials](#modular-arithmetic-essentials)
  - [Euler’s Totient Function  $\\varphi(n)$](#eulers-totient-function--varphin)
  - [Euler’s Theorem](#eulers-theorem)
  - [Fermat’s Little Theorem (특수형)](#fermats-little-theorem-특수형)
  - [RSA (1977, Rivest–Shamir–Adleman)](#rsa-1977-rivestshamiradleman)
  - [Beyond RSA (그 이후)](#beyond-rsa-그-이후)

---

# Number Theory II

## Encryption Basics (암호화 기초)

| 개념               | 한줄 요약                                              |
| ---------------- | -------------------------------------------------- |
| **Cryptology**   | *Art of hiding information* – 정보를 숨기는 기술           |
| **Encryption E** | 평문 $m$ → 암문 $c=E\_k(m)$                        |
| **Decryption D** | 암문 $c$ → 평문 $m=D\_k(c)$                        |
| **Security 목표**  | 키 $k$ 없이는 $c$에서 $m$에 대한 **어떤 정보도** 추론 못 해야 함 |

---

## Turing’s Code v1 (단순 곱셈 방식)

| 단계      | 설명                                                                   |
| ------- | -------------------------------------------------------------------- |
| Key     | 비밀 소수 $k$                                                          |
| Encrypt | $c = m\cdot k$                                                     |
| Decrypt | $m = c/k$ (키를 아는 경우)                                               |
| **취약점** | 서로 다른 암문 $c\_1,c\_2$ 두 개만 가로채면  …<br> $\gcd(c\_1,c\_2)=k$ → 키 노출 |

---

## Turing’s Code v2 (모듈러 곱셈)

1. **공개** 소수 $p$, **비밀** 소수 $k$ 공유
2. 암호화   $c = (m\cdot k)\bmod p$
3. **복호하려면** $k^{-1}\pmod{p}$ 필요

> **Known-Plaintext Attack**
> 평문 $m$과 암문 $c$ 한 쌍만 알아도
> $k^{-1}\equiv c\cdot m^{-1}\pmod p$
> 로부터 $k$ 계산 → 파괴.

---

## Modular Arithmetic Essentials

모듈러 산술의 핵(핵심 정의)

* **Congruence**   $x\equiv y\pmod n \iff n\mid(x-y)$
* **Multiplicative Inverse**   $x^{-1}$ such that $x x^{-1}\equiv1\pmod n$

  * 존재 조건 $\gcd(x,n)=1$ (→ 확장 Euclid로 계산)

---

## Euler’s Totient Function  $\varphi(n)$

*0 < $k$ < $n$ 중 $k$가 $n$과 서로소인 개수*

* 예) $\varphi(12)=4;(1,5,7,11)$
* 예) $\varphi(15)=8$

---

## Euler’s Theorem

서로소 $\gcd(k,n)=1$ 이면

$$
k^{\varphi(n)} \equiv 1 \pmod n
$$


1. $k$와 $n$에 서로소인 수들 ${k\_1,\dots,k\_r}$ ($r=\varphi(n)$) 고려
2. 곱셈 후 $k$를 곱하고 나서 ‘나머지 집합’이 다시 **동일 집합**임을 증명
3. 양변에서 곱셈 역원으로 소거 ⇒ 정리 성립

---

## Fermat’s Little Theorem (특수형)

소수 $p$과 $1\le k\le p-1$에 대해

$$
k^{\,p-1} \equiv 1 \pmod p
$$

> Euler 정리에서 $\varphi(p)=p-1$을 대입해 바로 얻음.
> 덕분에 $k^{-1}\equiv k^{,p-2}\pmod p$ 를 쉽게 구할 수 있다.

---

## RSA (1977, Rivest–Shamir–Adleman)

현대 공개키 암호의 출발점

| 단계             | 수식·설명                                                                                            |
| -------------- | ------------------------------------------------------------------------------------------------ |
| **1. KeyGen**  | 소수 $p,q$ 선택 → $n=pq$                                                                         |
|                | 공개지수 $e$ : $\gcd(e,\phi(n))=1$  ($\phi(n)=(p-1)(q-1)$)                                     |
|                | **공개키** $(e,n)$   **비밀키** $d\equiv e^{-1}\pmod{\phi(n)}$                                     |
| **2. Encrypt** | 평문 $m;(0 < m < n)$ → $c \equiv m^{,e}\pmod n$                                                  |
| **3. Decrypt** | $m \equiv c^{d}\pmod n$  ← (Fermat/Euler로 증명)                                                 |
| **보안 근거**      | $n$ 을 인수분해 $\Rightarrow$ $p,q$ 노출 $\Rightarrow$ $\phi(n)$ 계산 가능. 인수분해가 **어렵다**는 가정에 의존 |

---

## Beyond RSA (그 이후)

* **Craig Gentry (2009)** ― 첫 **전역적 동형암호**(FHE) 제시
* 2010년대 ― 모듈러 연산·격자 기반의 간단한 FHE 스킴 다수 등장

  * 암호문 상에서 **덧셈·곱셈** 수행 → 평문 연산과 동치

> 정수론의 도구(모듈러 곱, 역원, φ-함수)가 **현대 암호 전반**을 지탱한다.
