---
title: "Instru&#231;&#227;o Option Explicit (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Explicit"
  - "vb.OptionExplicit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarando variáveis, explicit"
  - "palavra-chave Explicit"
  - "declaração de variável explícita"
  - "declaração de variável forçada na instrução Option Explicit"
  - "instrução Option Explicit"
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Option Explicit (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Força a declaração explícita de todas as variáveis em um arquivo ou permite que as declarações implícitas de variáveis.  
  
## Sintaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## Partes  
 `On`  
 Opcional.  Permite verificação `Option Explicit`.  Se `On` ou `Off` não for especificado, o padrão é `On`.  
  
 `Off`  
 Opcional.  Desativa verificação `Option Explicit`.  
  
## Comentários  
 Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando a `Dim` ou `ReDim` instruções.  Se você tentar usar um nome de variável não declarado, ocorrerá um erro em tempo de compilação.  O `Option Explicit Off` instrução permite que a declaração implícita de variáveis.  
  
 Se usada, a declaração `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras declarações no código\-fonte.  
  
> [!NOTE]
>  Definindo `Option Explicit` para `Off` não é geralmente uma boa prática.  Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que poderia causar resultados inesperados quando o programa é executado.  
  
## Quando não está presente de uma instrução Option Explicit  
 Se o código\-fonte não contém um `Option Explicit` instrução, o  **Option Explicit** definição na [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) é usado.  Se o compilador de linha de comando for usado, o [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador é usada.  
  
#### Para definir Option Explicit no IDE  
  
1.  Em **Solution Explorer**, selecione um projeto.  No menu **Project**, clique em **Properties**..  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique na guia **Compile**.  
  
3.  Defina o valor no  **Option Explicit** caixa.  
  
 Quando você cria um novo projeto, o  **Option Explicit** definição na  **Compilar** for definido como o  **Option Explicit** definição na  **Padrões de VB** caixa de diálogo.  Para acesso a  **Padrões de VB** caixa de diálogo, diante a  **Ferramentas** menu, clique em  **Opções**.  No  **Opções** caixa de diálogo caixa, expanda  **projetos e soluções**e, em seguida, clique em  **Padrões de VB**.  A configuração padrão inicial no  **Padrões de VB** é `On`.  
  
#### Para definir Option Explicit na linha de comando  
  
-   Inclua a opção de compilador [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) no comando **vbc**.  
  
## Exemplo  
 O exemplo a seguir usa a `Option Explicit` a instrução para forçar uma declaração explícita de todas as variáveis.  Tentando usar uma variável não declarada causa um erro em tempo de compilação.  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## Consulte também  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)