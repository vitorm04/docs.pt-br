---
title: "/optioninfer | Microsoft Docs"
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
  - "/optioninfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /optioninfer [Visual Basic]"
  - "Opção de compilador optioninfer [Visual Basic]"
  - "Opção de compilador -optioninfer [Visual Basic]"
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optioninfer
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permite o uso de inferência de tipo local nas declarações de variáveis.  
  
## Sintaxe  
  
```  
/optioninfer[+ | -]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Termo|Definição|  
|`+`  &#124; `-`|Opcional.  Especifique `/optioninfer+` para habilitar a inferência de tipo de local ou `/optioninfer-` para bloqueá\-la.  A opção `/optioninfer`, sem valor especificado, é a mesma de `/optioninfer+`.  O valor padrão quando o comutador `/optioninfer` não estiver presente também é `/optioninfer+`.  O valor padrão é definido no arquivo de resposta Vbc.rsp.|  
  
> [!NOTE]
>  Você pode usar a opção `/noconfig` para manter os padrões internos do compilador em vez dos especificados no vbc.rsp.  O padrão do compilador para essa opção é `/optioninfer-`.  
  
## Comentários  
 Se o arquivo de código\-fonte tiver um [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md), a instrução substitui a configurações do compilador de linha de comando `/optioninfer`.  
  
### Para definir \/optioninfer no IDE do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de Soluções**.  No menu **Projeto**, clique em **Propriedades**.  Para obter mais informações, consulte [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/pt-br/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Na guia **Compilar**, modifique o valor na caixa **Option infer**.  
  
## Exemplo  
 O seguinte código compila `test.vb` com a inferência de tipo local habilitada.  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Compilando a partir da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)