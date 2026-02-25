# ADD & SUB

Essas instruções fazem o que é esperado: Adicionam ou Subtraem valores.

### ADD

1. CPU lê `destino`
2. CPU lê `fonte`
3. soma: `resultado = destino + fonte`
4. grava resultado em `destino`
5. atualiza flags

***

### ✔️ SUB

1. CPU lê `destino`
2. CPU lê `fonte`
3. subtrai: `resultado = destino - fonte`
4. grava resultado em `destino`
5. atualiza flags

Operações validas:

| Destino     | Fonte       | Válido? |
| ----------- | ----------- | ------- |
| Registrador | Registrador | ✔️      |
| Registrador | Imediato    | ✔️      |
| Registrador | Memória     | ✔️      |
| Memória     | Registrador | ✔️      |
| Memória     | Imediato    | ✔️      |
| Memória     | Memória     | ❌       |

{% hint style="warning" %}
Assim como no MOV não existe operação de Memória para Memória
{% endhint %}

## ADD

Adiciona o valor e grava no destino.

### Syntax

```asm
add destino, fonte
```

Significa:

```
destino = destino + fonte
```

## SUB

Subtrai o valor e grava no destino.

### Syntax

```asm
sub destino, fonte
```

Significa:

```
destino = destino - fonte
```
