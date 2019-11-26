---
title: Instrução Option Strict
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: a002526a107fdc6e8e02890d11db94a3d224c94b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353761"
---
# <a name="option-strict-statement"></a>Instrução Option Strict
Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`On`|Opcional. Enables `Option Strict` checking.|  
|`Off`|Opcional. Disables `Option Strict` checking.|  
  
## <a name="remarks"></a>Comentários  
 When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:  
  
- Conversões de estreitamento implícitas  
  
- Associação tardia  
  
- Digitação implícita que resulta em um tipo `Object`  
  
> [!NOTE]
> In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error. For information about how to use these settings, see [To set warning configurations in the IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) later in this topic.  
  
 The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings. The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.  
  
 If used, the `Option Strict` statement must appear before any other code statements in a file.  
  
 When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements. Data types can be specified explicitly, or specified by using local type inference. Specifying data types for all your programming elements is recommended, for the following reasons:  
  
- It enables IntelliSense support for your variables and parameters. This enables you to see their properties and other members as you type code.  
  
- It enables the compiler to perform type checking. Type checking helps you find statements that can fail at run time because of type conversion errors. It also identifies calls to methods on objects that do not support those methods.  
  
- It speeds up the execution of code. One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type. Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicit Narrowing Conversion Errors  
 Erros de conversão de redução implícita ocorrerem quando há uma conversão de tipo de dados implícita que é uma conversão de redução.  
  
 Visual Basic can convert many data types to other data types. Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity. A run-time error occurs if such a narrowing conversion fails. `Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them. For more information, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Conversions that can cause errors include implicit conversions that occur in expressions. Para mais informações, consulte os seguintes tópicos:  
  
- [Operador +](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Tipo de Dados de Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 When you concatenate strings by using the [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), all conversions to the strings are considered to be widening. So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.  
  
 When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on. You can avoid the compile-time error by using a widening conversion or an explicit conversion.  
  
 Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable. This occurs even if `Option Strict` is on. For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Late Binding Errors  
 Um objeto tem associação tardia quando é atribuído a uma propriedade ou a um método de uma variável declarada como sendo do tipo `Object`. For more information, see [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Implicit Object Type Errors  
 Erros de tipo de objeto implícitos ocorrem quando um tipo apropriado não pode ser inferido de uma variável declarada, portanto, um tipo de `Object` é inferido. Isso ocorre principalmente quando você usa uma instrução `Dim` para declarar uma variável sem usar uma cláusula `As` e `Option Infer` está desativado. For more information, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).  
  
 For method parameters, the `As` clause is optional if `Option Strict` is off. However, if any one parameter uses an `As` clause, they all must use it. If `Option Strict` is on, the `As` clause is required for every parameter definition.  
  
 If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`. No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on. An example of this is `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Tipos de Dados e Valores Padrão  
 The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Tipo de dados especificado?|Inicializador especificado?|Exemplo|Resultado|  
|---|---|---|---|  
|Não|Não|`Dim qty`|Se o `Option Strict` estiver desativado (padrão), a variável é definida como `Nothing`.<br /><br /> Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Não|Sim|`Dim qty = 5`|Se `Option Infer` estiver ativado (padrão), a variável usa o tipo de dados do inicializador. See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Sim|Não|`Dim qty As Integer`|A variável é inicializada para o valor padrão para o tipo de dados. For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Sim|Sim|`Dim qty  As Integer = 5`|Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>When an Option Strict Statement Is Not Present  
 If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used. The **Compile Page** has settings that provide additional control over the conditions that generate an error.  
  
 If you are using the command-line compiler, you can use the [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>To set Option Strict in the IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. No **Gerenciador de Soluções**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**.  
  
2. On the **Compile** tab, set the value in the **Option Strict** box.  
  
### <a name="conditions"></a> To set warning configurations in the IDE  
 When you use the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors. The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on. A seguir estão estas configurações:  
  
- **Conversão implícita**  
  
- **Associação tardia; a chamada poderia falhar no tempo de execução**  
  
- **Tipo implícito; objeto assumido**  
  
 Quando você define **Opção Estrita** como **Ativada**, todas estas três definições de configuração de aviso são definidas como **Erro**. Quando você define **Opção Estrita** como **Desativada**, todas as três configurações são definidas como **Nenhum**.  
  
 Você pode alterar individualmente cada definição de configuração de aviso como **Nenhum**, **Aviso** ou **Erro**. Se todas as três definições de configuração de aviso estiverem definidas como **Erro**, `On` aparecerá na caixa `Option strict`. Se todas as três estiverem definidas como **Nenhum**, `Off` será exibido nessa caixa. Para qualquer outra combinação dessas configurações, **(personalizado)** será exibido.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>To set the Option Strict default setting for new projects  
 When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.  
  
 To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. The initial default setting in **VB Defaults** is `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>To set Option Strict on the command line  
 Include the [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.  
  
## <a name="example"></a>Exemplo  
 The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions. This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Exemplo  
 The following example demonstrates a compile-time error caused by late binding. This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Exemplo  
 The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`. This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Consulte também

- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Página de Compilação, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Como acessar membros de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Vinculação tardia em soluções do Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
