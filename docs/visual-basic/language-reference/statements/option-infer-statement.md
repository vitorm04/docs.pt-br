---
title: Instrução Option Infer
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: c7628e5c4c0cda527a4c3b1a211c45760640fc63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="option-infer-statement"></a>Instrução Option Infer
Permite o uso de inferência de tipo local ao declarar variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`On`|Opcional. Permite inferência de tipo local.|  
|`Off`|Opcional. Desabilita inferência de tipo local.|  
  
## <a name="remarks"></a>Comentários  
 Para definir `Option Infer` em um arquivo, digite `Option Infer On` ou `Option Infer Off` na parte superior do arquivo, antes de qualquer outro código-fonte. Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.  
  
 Quando você define `Option Infer` para `On`, você pode declarar variáveis locais sem especificar explicitamente um tipo de dados. O compilador infere o tipo de dados de uma variável do tipo de sua expressão de inicialização.  
  
 Na ilustração a seguir, `Option Infer` está ativado. A variável na declaração `Dim someVar = 2` é declarada como um inteiro por inferência de tipo.  
  
 ![Exibição do IntelliSense da declaração. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
IntelliSense quando o Option Infer está ligado  
  
 Na ilustração a seguir, o `Option Infer` está desativado. A variável na declaração `Dim someVar = 2` é declarada como um `Object` por inferência de tipo. Neste exemplo, o **Option Strict** configuração é definida como **Off** no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 ![Exibição do IntelliSense da declaração. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
IntelliSense quando o Option Infer está desligado  
  
> [!NOTE]
>  Quando uma variável é declarada como um `Object`, o tipo de tempo de execução pode ser alterado enquanto o programa está sendo executado. Visual Basic executa operações chamadas *boxing* e *unboxing* para converter entre um `Object` e um tipo de valor, o que torna a execução mais lenta. Para obter informações sobre conversão boxing e unboxing, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 A inferência de tipo aplica-se no nível do procedimento e não fora de um procedimento em uma classe, estrutura, módulo ou interface.  
  
 Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Quando uma Instrução Option Infer Não Está Presente  
 Se o código-fonte não contém um `Option Infer` instrução, o **Option Infer** definição no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado. Se o compilador de linha de comando é usado, o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador é usada.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Para definir o Option Infer no IDE  
  
1.  No **Gerenciador de Soluções**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique na guia **Compilar**.  
  
3.  Definir o valor no **Option infer** caixa.  
  
 Quando você cria um novo projeto, o **Option Infer** definição no **compilar** for definido como o **Option Infer** definindo no **padrões VB** caixa de diálogo. Para acessar o **padrões VB** caixa de diálogo de **ferramentas** menu, clique em **opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. A configuração inicial padrão na **padrões VB** é `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Para definir o Option Infer na linha de comando  
  
-   Incluir o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador no **vbc** comando.  
  
## <a name="default-data-types-and-values"></a>Tipos de Dados e Valores Padrão  
 A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.  
  
|Tipo de dados especificado?|Inicializador especificado?|Exemplo|Resultado|  
|---|---|---|---|  
|Não|Não|`Dim qty`|Se o `Option Strict` estiver desativado (padrão), a variável é definida como `Nothing`.<br /><br /> Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Não|Sim|`Dim qty = 5`|Se `Option Infer` estiver ativado (padrão), a variável usa o tipo de dados do inicializador. Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Sim|Não|`Dim qty As Integer`|A variável é inicializada para o valor padrão para o tipo de dados. Para obter mais informações, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Sim|Sim|`Dim qty  As Integer = 5`|Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.|  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir demonstram como a instrução `Option Infer` habilita a inferência de tipo local.  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o tipo de tempo de execução pode ser diferente quando uma variável é identificada como um `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Conversão boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
