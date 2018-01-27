```sh
var('mu_0 mu_m1 mu_p1')
var('A B C k x gamma_ E L')
```

```sh
E,L,gamma_=100,1,1
mu_0,mu_m1,mu_p1=1,2,3
```

```sh
def T(m1,m2): return (m1/m2)/((m1/m2)-1)
```

```sh
M=matrix([[mu_0,0,0],[0,mu_m1,0],[0,0,mu_p1]])
show(M)
```

```sh
sigm1=matrix([[0,-1,0],[1,0,0],[0,0,0]])
sigm2=matrix([[0,0,-1],[0,0,0],[1,0,0]])
sigm3=matrix([[0,0,0],[0,0,1],[0,-1,0]])
show(sigm1);show(sigm2);show(sigm3)
```

```sh
psi=matrix([[A],[B],[C]])*exp(i*k*x)
show(psi)
```

```sh
H=-identity_matrix(3)*diff(psi,x,2) +M*M*psi + sigm1*gamma_*(-i*T(mu_0,mu_m1)*mu_m1^2*(1/4)*psi$
show(H)
H=H.list()
```

```sh
H[0]=H[0].collect(A).collect(B).collect(C);show(H[0])
H[1]=H[1].collect(A).collect(B).collect(C);show(H[1])
H[2]=H[2].collect(A).collect(B).collect(C);show(H[2])
```

```sh
solA=solve(H[0],A,solution_dict=True)
eq1=H[1].subs(A=solA[0][A]);show(eq1)
eq2=H[2].subs(A=solA[0][A]);show(eq2)
```

```sh
solB=solve(eq1,B,solution_dict=True)
eq3=eq2.subs(B=solB[0][B]);show(eq3)
```

```sh
solA[0][A]=solA[0][A].subs(B=solB[0][B]);
show(solA);
show(solB);
```

```sh
ks=solve(eq3,k,solution_dict=True)
```

```sh
k1=n(ks[0][k]).real();show(k1)
k2=n(ks[1][k]).real();show(k2)
k3=n(ks[2][k]).imag()*i;show(k3)
k4=n(ks[3][k]).imag()*i;show(k4)
k5=n(ks[4][k]).real();show(k5)
k6=n(ks[5][k]).real();show(k6)
```

```sh
eq1=H[0].subs(E=k^2+mu_0^2);show(eq1)
eq2=H[1].subs(E=k^2+mu_0^2);show(eq2)
eq3=H[2].subs(E=k^2+mu_0^2);show(eq3)
```

```sh
sol=solve([eq1,eq2,eq3],A,B,C,solution_dict=True)
sol
```

```sh
var('A1 A2 A3 A4 A5 A6 B1 B2 B3 B4 B5 B6 C1 C2 C3 C4 C5 C6')
A1=solA[0][A].subs(C=C1).subs(k=k1)
A2=solA[0][A].subs(C=C2).subs(k=k2)
A3=solA[0][A].subs(C=C3).subs(k=k3)
A4=solA[0][A].subs(C=C4).subs(k=k4)
A5=solA[0][A].subs(C=C5).subs(k=k5)
A6=solA[0][A].subs(C=C6).subs(k=k6)

B1=solB[0][B].subs(C=C1).subs(k=k1)
B2=solB[0][B].subs(C=C2).subs(k=k2)
B3=solB[0][B].subs(C=C3).subs(k=k3)
B4=solB[0][B].subs(C=C4).subs(k=k4)
B5=solB[0][B].subs(C=C5).subs(k=k5)
B6=solB[0][B].subs(C=C6).subs(k=k6)

psi2=matrix([[A1*exp(i*k1*x)+A2*exp(i*k2*x)+A3*exp(i*k3*x)+A4*exp(i*k4*x)+A5*exp(i*k5*x)+A6*exp$
show(psi2)
```
