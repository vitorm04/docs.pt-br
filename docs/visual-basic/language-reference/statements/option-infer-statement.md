---
title: "Instrução Option Infer | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement
- Infer keyword
- declaring variables, inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e6074ad44b94c80f275af562edef2dcd1173c0c3
ms.lasthandoff: 03/13/2017

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
  
 ![Exibição do IntelliSense da declaração.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
IntelliSense quando o Option Infer está ligado  
  
 Na ilustração a seguir, o `Option Infer` está desativado. A variável na declaração `Dim someVar = 2` é declarada como um `Object` por inferência de tipo. Neste exemplo, o **Option Strict** configuração é definida como **Off** no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 ![Exibição do IntelliSense da declaração.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
IntelliSense quando o Option Infer está desligado  
  
> [!NOTE]
>  Quando uma variável é declarada como um `Object`, o tipo de tempo de execução pode ser alterado enquanto o programa está sendo executado. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]executa operações chamadas *conversão boxing* e *unboxing* para converter entre um `Object` e um tipo de valor, o que torna a execução mais lenta. Para obter informações sobre conversões boxing e unboxing, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification.md).  
  
 A inferência de tipo aplica-se no nível do procedimento e não fora de um procedimento em uma classe, estrutura, módulo ou interface.  
  
 Para obter informações adicionais, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Quando uma Instrução Option Infer Não Está Presente  
 Se o código-fonte não contém um `Option Infer` instrução, o **Option Infer** definição no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado. Se o compilador de linha de comando é usado, o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador é usada.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Para definir o Option Infer no IDE  
  
1.  Em **Solution Explorer**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [NIB: Gerenciando propriedades do projeto com o Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Clique na guia **Compilar**.  
  
3.  Defina o valor no **Option infer** caixa.  
  
 Quando você cria um novo projeto, o **Option Infer** definição no **compilar** for definido como o **Option Infer** definindo no **padrões de VB** caixa de diálogo. Para acessar o **padrões de VB** caixa de diálogo de **ferramentas** menu, clique em **opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. A configuração inicial padrão em **padrões de VB** é `On`.  
  
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
  
 [!code-vb[VbVbalrTypeInference n º&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o tipo de tempo de execução pode ser diferente quando uma variável é identificada como um `Object`.  
  
 [!code-vb[VbVbalrTypeInference n º&11;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Caixa de diálogo de opções de padrões, projetos do Visual Basic](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Conversão boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
