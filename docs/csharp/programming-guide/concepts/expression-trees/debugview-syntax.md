---
title: Sintaxe usada pela propriedade DebugView (C#)
description: Descreve a sintaxe especial usada pela propriedade DebugView para produzir uma representação de cadeia de caracteres de árvores de expressão
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: de82a738430cdd37c4905a5ae7da5faeb46f00a4
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196362"
---
# <a name="debugview-syntax"></a>Sintaxe de `DebugView`

A propriedade `DebugView` (disponível apenas durante a depuração) fornece uma renderização de cadeia de caracteres de árvores de expressão. A maior parte da sintaxe é bastante simples de entender; os casos especiais são descritos nas seções a seguir.

Cada exemplo é seguido por um comentário de bloco, que contém `DebugView`. 

## <a name="parameterexpression"></a>ParameterExpression 

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> os nomes de variáveis são exibidos com o símbolo `$` no início.
  
Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.
  
### <a name="examples"></a>Exemplos

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a>ConstantExpression  

Para objetos <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.  
  
Para tipos numéricos que têm sufixos padrão como literais de C#, o sufixo é adicionado ao valor. A tabela a seguir mostra os sufixos associados com vários tipos numéricos.  

| Tipo | Palavra-chave | Sufixo |  
|--|--|--|  
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/keywords/uint.md) | U |  
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/keywords/long.md) | L |  
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/keywords/ulong.md) | UL |  
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/keywords/double.md) | D |  
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/keywords/float.md) | F |  
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/keywords/decimal.md) | M |  
  
### <a name="examples"></a>Exemplos  

```csharp
int num = 10; 
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10; 
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a>BlockExpression
 
Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> difere do tipo da última expressão no bloco, o tipo será exibido entre colchetes angulares (`<` e `>`). Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.  
  
### <a name="examples"></a>Exemplos  

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a>LambdaExpression

Objetos <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> são exibidos junto com seus tipos delegados.
  
Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.
  
### <a name="examples"></a>Exemplos

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```
  
## <a name="labelexpression"></a>LabelExpression

Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.
  
O token `.Label` indica o início do rótulo. O token `.LabelTarget` indica o local para o qual o destino deve saltar.
  
Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.
  
### <a name="examples"></a>Exemplos

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```
  
## <a name="checked-operators"></a>Operadores verificados  

Os operadores verificados são exibidos com o símbolo `#` na frente do operador. Por exemplo, o operador de adição verificado é exibido como `#+`.  
  
### <a name="examples"></a>Exemplos  

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```