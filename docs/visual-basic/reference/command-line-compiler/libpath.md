---
title: "/libpath | Microsoft Docs"
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
  - "Opção de compilador /libpath [Visual Basic]"
  - "Opção de compilador libpath [Visual Basic]"
  - "Opção de compilador -libpath [Visual Basic]"
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /libpath
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica a localização das montagens referenciadas  
  
## Sintaxe  
  
```  
/libpath:dirList  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`dirList`|Obrigatório.  A lista de diretórios delimitada por ponto\-e\-vírgula para o compilador ver se algum assembly referenciado não é encontrado ou no diretório de trabalho corrente \(o diretório de onde você está chamando o compilador\) ou o diretório do commn language runtime.  Se o nome do diretório contém um espaço, delimite o nome entre aspas \(" "\).|  
  
## Comentários  
 A opção `/libpath` especifica a localização das montagens referenciadas pela opção [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md).  
  
 O compilador procura por referências de montagem que não correspondem completamente às exigências na seguinte ordem:  
  
1.  Diretório de trabalho corrente.  Este é o diretório do qual o compilador é chamado.  
  
2.  O diretório do sistema common language runtime.  
  
3.  Diretórios especificados por `/libpath`.  
  
4.  Diretórios especificados pela variável de ambiente LIB.  
  
 A opção  `/libpath` é aditiva; especificando\-a mais de uma vez acrescenta a valores anteriores.  
  
 Use `/reference` para especificar uma referência de montagem  
  
||  
|-|  
|Configurar \/libpath no ambiente de desenvolvimento integrado Visual Studio|  
|1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, clique em **Properties**..  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na aba **References**.<br />3.  Clique no botão **Reference Paths...**.<br />4.  Na caixa de diálogo **Reference Paths**, insira o nome do diretório na caixa **Folder:**<br />5.  Clique em **Add Folder**.|  
  
## Exemplo  
 O seguinte código compilar `T2.vb` para criar um arquivo .exe.  O compilador procura por referências de montagens no diretório de trabalho, no diretório raiz do drive C:, e no novo diretório das montagens.  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## Consulte também  
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)