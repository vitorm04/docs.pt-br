---
title: "Depurando árvores de expressão no Visual Studio (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: efbd8c19947c45b3ba15ce7b574000d56526ef45
ms.lasthandoff: 03/13/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Depurando árvores de expressão no Visual Studio (Visual Basic)
Quando você depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão. Para obter uma visão geral da estrutura de árvore de expressão, você pode usar o `DebugView` propriedade, que está disponível apenas no modo de depuração. Para obter mais informações sobre depuração, consulte [depuração no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).  
  
 Para melhor representar o conteúdo das árvores de expressão, o `DebugView` propriedade usa os visualizadores do Visual Studio. Para obter mais informações, consulte [criar os visualizadores personalizados](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Para abrir um visualizador para uma árvore de expressão  
  
1.  Clique no ícone de lupa que aparece ao lado de `DebugView` propriedade de uma árvore de expressão em **DataTips**, um **inspeção** janela, o **Autos** janela, ou o **locais** janela.  
  
     Uma lista de visualizadores é exibida.  
  
2.  Clique no visualizador que você deseja usar.  
  
 Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression>nomes de variáveis são exibidos com um símbolo "$" no início.</xref:System.Linq.Expressions.ParameterExpression>  
  
 Se um parâmetro não tem um nome, ele é atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.  
  
### <a name="examples"></a>Exemplos  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     Propriedade `DebugView`  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     Propriedade `DebugView`  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Para <xref:System.Linq.Expressions.ConstantExpression>objetos que representam valores inteiros, cadeias de caracteres, e `null`, o valor da constante é exibido.</xref:System.Linq.Expressions.ConstantExpression>  
  
### <a name="examples"></a>Exemplos  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     Propriedade `DebugView`  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     Propriedade `DebugView`  
  
     10D  
  
## <a name="blockexpression"></a>BlockExpression  
 Se o tipo de uma <xref:System.Linq.Expressions.BlockExpression>objeto difere do tipo da última expressão no bloco, o tipo é exibido no `DebugInfo` propriedade entre colchetes angulares (\< e >).</xref:System.Linq.Expressions.BlockExpression> Caso contrário, o tipo do <xref:System.Linq.Expressions.BlockExpression>objeto não é exibido.</xref:System.Linq.Expressions.BlockExpression>  
  
### <a name="examples"></a>Exemplos  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     Propriedade `DebugView`  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     Propriedade `DebugView`  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression>objetos são exibidos junto com os tipos de delegado.</xref:System.Linq.Expressions.LambdaExpression>  
  
 Se uma expressão lambda não tem um nome, ele é atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.  
  
### <a name="examples"></a>Exemplos  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     Propriedade `DebugView`  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     Propriedade `DebugView`  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 Se você especificar um valor padrão para o <xref:System.Linq.Expressions.LabelExpression>do objeto, esse valor é exibido antes do <xref:System.Linq.Expressions.LabelTarget>objeto.</xref:System.Linq.Expressions.LabelTarget> </xref:System.Linq.Expressions.LabelExpression>  
  
 O `.Label` token indica o início do rótulo. O `.LabelTarget` token indica o destino de saltar para o destino.  
  
 Se um rótulo não tem um nome, ele é atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.  
  
### <a name="examples"></a>Exemplos  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     Propriedade `DebugView`  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     Propriedade `DebugView`  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a>Operadores de verificação  
 Operadores de verificação é exibido com o símbolo "#" na frente do operador. Por exemplo, o operador de adição verificado é exibido como `#+`.  
  
### <a name="examples"></a>Exemplos  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     Propriedade `DebugView`  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     Propriedade `DebugView`  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>Consulte também  
 [Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Depurando no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [Criar visualizadores personalizados](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)
