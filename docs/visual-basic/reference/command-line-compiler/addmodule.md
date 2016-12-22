---
title: "/addmodule- | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /addmodule [Visual Basic]"
  - "Opção de compilador addmodule [Visual Basic]"
  - "Opção de compilador -addmodule [Visual Basic]"
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /addmodule
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Faz com que o compilador fazer todas as informações dos arquivos especificados disponíveis para o projeto que você está compilando atualmente de tipo.  
  
## Sintaxe  
  
```  
/addmodule:fileList  
```  
  
## Arguments  
 `fileList`  
 Obrigatório. Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos assembly. Nomes de arquivo que contêm espaços devem estar entre aspas \(""\).  
  
## Comentários  
 Os arquivos listados pelo `fileList` parâmetro deve ser criado com o `/target:module` opção, ou com o equivalente do outro compilador `/target:module`.  
  
 Todos os módulos adicionados com `/addmodule` deve estar no mesmo diretório que o arquivo de saída em tempo de execução. Ou seja, você pode especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução. Se não for, você obterá um <xref:System.TypeLoadException> erro.  
  
 Se você especificar \(implícita ou explicitamente\) qualquer[\/target](../../../visual-basic/reference/command-line-compiler/target.md) opção diferente de `/target:module` com `/addmodule`, os arquivos que você passar para `/addmodule` se tornam parte do assembly do projeto. Um assembly é necessário para executar um arquivo de saída que tem um ou mais arquivos adicionados com `/addmodule`.  
  
 Use [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) para importar metadados de um arquivo que contém um assembly.  
  
> [!NOTE]
>  O `/addmodule` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir cria um módulo.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 O código a seguir importa tipos do módulo.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Quando você executa `t1`, ele produz `802`.  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)