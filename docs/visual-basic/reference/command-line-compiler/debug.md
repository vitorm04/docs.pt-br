---
title: "/debug (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Opção de compilador /debug [Visual Basic]"
  - "Opção de compilador debug [Visual Basic]"
  - "Opção de compilador -debug [Visual Basic]"
  - "opções de compilador debug"
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /debug (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Faz o compilador gerar informações de depuração e colocá\-lo nos arquivos de saída.  
  
## Sintaxe  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`+`  &#124; `-`|Opcional.  Especificando `+` ou `/debug` faz com que o compilador gerar informações de depuração e colocá\-lo em um arquivo. PDB.  Especificando `-` tem o mesmo efeito que não especificando `/debug`.|  
|`full`  &#124; `pdbonly`|Opcional.  Especifica o tipo de informações de depuração gerados pelo compilador.  Se você não especificar `/debug:pdbonly`, o padrão é `full`, que permite anexar um depurador para o programa em execução.  O `pdbonly` argumento permite a depuração de código\-fonte quando o programa for iniciado no depurador, mas ele exibe o código de linguagem assembly somente quando o programa em execução está anexado ao depurador.|  
  
## Comentários  
 Use esta opção para criar compilações de depuração.  Se você não especificar `/debug`, `/debug+`, ou `/debug:full`, não será possível depurar o arquivo de saída do seu programa.  
  
 Por padrão, as informações de depuração não é emitida \(`/debug-`\).  Para emitir informações de depuração, especifique `/debug` ou `/debug+`.  
  
 Para obter informações sobre como configurar o desempenho de depuração de um aplicativo, consulte [Facilitando a depuração de uma imagem](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  
  
||  
|-|  
|Para definir o Visual Studio \/debug ambiente de desenvolvimento integrado|  
|1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Compile**.<br />3.  Clique em  **Opções avançadas de compilação**.<br />4.  Modificar o valor de  **Gerar informações de depuração** caixa.|  
  
## Exemplo  
 O exemplo a seguir coloca as informações de depuração no arquivo de saída `App.exe`.  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)