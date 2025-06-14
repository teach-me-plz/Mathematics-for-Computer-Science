## 목차

- [Number Theory](#number-theory)

---

# Number Theory

물병 문제로부터 시작되어 만들어진 하나의 정리

$$
\boxed{\;
\gcd(a,b)=
\min\{\,sa+tb>0\mid s,t\in\mathbb Z\}
\;}
$$

**“ $a,b$ 의 최대공약수는 $a$와 $b$로 만들 수 있는 양수 선형결합(물의 양) 중 가장 작은 값이다 ”**   

물병 문제 증명   

1. **(Invariant) $\gcd(a,b)$ 는 항상 유지된다**
   – 어떤 붓기·비우기·옮기기를 해도 결과 물의 양은 $\gcd(a,b)$ 의 배수   

2. **모든 도달가능 상태 = 선형결합 $sa+tb$**
   – 상태 머신으로 “채우기·비우기·붓기” 규칙을 형식화하여 증명   

3. **$\gcd(a,b)$ 자체도 선형결합이 된다**
   – 확장 유클리드 알고리즘(및 귀납 불변식)으로 $sa+tb=\gcd(a,b)$ 를 구성   

두 번째·세 번째 성질을 합치면 “선형결합으로 실제로 만들 수 있는 값들 중 최솟값이 바로 $\gcd(a,b)$” 가 되어 위의 정리가 완성   

