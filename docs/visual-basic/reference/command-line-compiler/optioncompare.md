---
title: "/optioncompare | Microsoft Docs"
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
  - "/optioncompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /optioncompare [Visual Basic]"
  - "Opção de compilador optioncompare [Visual Basic]"
  - "Opção de compilador -optioncompare [Visual Basic]"
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optioncompare
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica como são feitas comparações de cadeias de caracteres.  
  
## Sintaxe  
  
```  
/optioncompare:{binary | text}  
```  
  
## Comentários  
 Você pode especificar `/optioncompare` em uma da duas formas: `/optioncompare:binary` para usar comparações binárias de cadeias de caracteres e `/optioncompare:text` para usar comparações de cadeias de caracteres de texto.  Por padrão,  o compilador utiliza `/optioncompare:binary`.  
  
 No Microsoft Windows, a página de código que está sendo utilizada determina a ordem de classificação binária.  Uma ordem de classificação binária típica é como se segue:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Comparações baseadas em texto de cadeias de caracteres são baseadas numa ordem de classificação de texto que não diferencia maiúsculas de minúsculas, determinada pelo local do seu sistema.  Uma ordem de classificação de texto típica é como se segue:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### Para configurar \/optioncompare no IDE do Visual Studio  
  
1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, clique em **Properties**..  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique na guia **Compile**.  
  
3.  Modifique o valor na caixa **Option Compare**.  
  
### Para configurar \/optiocompare programaticamente  
  
-   Consulte [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## Exemplo  
 O código a seguir compila P`rojFile.vb` e usa comparações binárias de cadeias de caracteres.  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)