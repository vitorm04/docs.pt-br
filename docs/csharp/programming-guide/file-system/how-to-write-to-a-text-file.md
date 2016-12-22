---
title: "Como escrever em um arquivo de texto (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TextWriter.WriteLine"
  - "StreamWriter.Close"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "arquivos [C#], arquivos de texto"
  - "texto, escrevendo em arquivos [C#]"
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como escrever em um arquivo de texto (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Estes exemplos mostram várias maneiras de gravar textos em um arquivo.  Os dois primeiros exemplos usam métodos de conveniência estáticos na <xref:System.IO.File?displayProperty=fullName> classe para gravar cada elemento de qualquer IEnumerable \< string \> e uma cadeia de caracteres em um arquivo de texto.  Exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente como gravar no arquivo.  Exemplos de 1 a 3 substituir todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto a um arquivo existente.  
  
 Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.  Você também pode usar o c\# [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) recurso.  
  
## Exemplo  
 [!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.  Você também pode usar o c\# [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) recurso.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo existe e é somente leitura.  
  
-   O nome do caminho pode ser muito longo.  
  
-   O disco pode estar cheio.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [exemplo: salvar uma coleção no armazenamento de aplicativos](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)