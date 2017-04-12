---
title: "Opção Explicit Statement (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
dev_langs:
- VB
helpviewer_keywords:
- declaring variables, explicit
- forced variable declaration in Option Explicit statement
- Explicit keyword
- explicit variable declaration
- Option Explicit statement
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 020f12f1fbb9a06647215f1fac6324e3b74e8a77
ms.lasthandoff: 03/13/2017

---
# <a name="option-explicit-statement-visual-basic"></a>Instrução Option Explicit (Visual Basic)
Força a declaração explícita de todas as variáveis em um arquivo ou permite declarações implícitas de variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Partes  
 `On`  
 Opcional. Permite `Option Explicit` verificação. Se `On` ou `Off` não for especificado, o padrão é `On`.  
  
 `Off`  
 Opcional. Desabilita `Option Explicit` verificação.  
  
## <a name="remarks"></a>Comentários  
 Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando a `Dim` ou `ReDim` instruções. Se você tentar usar um nome de variável não declarado, ocorrerá um erro em tempo de compilação. O `Option Explicit Off` instrução permite declarações implícitas de variáveis.  
  
 Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.  
  
> [!NOTE]
>  Definindo `Option Explicit` para `Off` geralmente não é uma boa prática. Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Quando uma instrução Option Explicit não está presente  
 Se o código-fonte não contém um `Option Explicit` instrução, o **Option Explicit** definição no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado. Se o compilador de linha de comando é usado, o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador é usada.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Para definir Option Explicit no IDE  
  
1.  Em **Solution Explorer**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique na guia **Compilar**.  
  
3.  Defina o valor no **Option Explicit** caixa.  
  
 Quando você cria um novo projeto, o **Option Explicit** definição no **compilar** for definido como o **Option Explicit** definindo no **padrões de VB** caixa de diálogo. Para acessar o **padrões de VB** caixa de diálogo de **ferramentas** menu, clique em **opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. A configuração inicial padrão em **padrões de VB** é `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Para definir Option Explicit na linha de comando  
  
-   Incluir o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador no **vbc** comando.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Option Explicit` instrução para forçar a declaração explícita de todas as variáveis. Tentativa de usar uma variável não declarada causa um erro em tempo de compilação.  
  
 [!code-vb[47 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[48 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução reDim](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
