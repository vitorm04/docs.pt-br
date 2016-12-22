---
title: "Como usar o My Namespace (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, acesso ao namespace My"
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar o My Namespace (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.MyServices> espaço para nome \(`My` em Visual Basic\) fornece acesso fácil e intuitivo para um número de.Classes do NET Framework, permitindo que você escrever código que interage com o computador, aplicativos, configurações, recursos e assim por diante.  Embora projetado originalmente para uso com o Visual Basic, o `MyServices` espaço para nome pode ser usado em aplicativos de C\#.  
  
 Para obter mais informações sobre como usar o `MyServices` espaço para nome do Visual Basic, consulte [Desenvolvimento com My](../../../visual-basic/reference/command-line-compiler/index.md).  
  
## Adicionando uma referência  
 Antes de usar o `MyServices` classes em sua solução, você deve adicionar uma referência à biblioteca de Visual Basic.  
  
#### Para adicionar uma referência à biblioteca de Visual Basic  
  
1.  Em  **Solution Explorer**, com o botão direito do  **referências** nó e selecione  **Add Reference**.  
  
2.  Quando o  **referências** caixa de diálogo for exibida, role para baixo na lista e selecione o Microsoft.VisualBasic.dll.  
  
     Também convém incluir a seguinte linha na `using` seção no início do seu programa.  
  
     [!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## Exemplo  
 Este exemplo chama vários métodos estáticos contidos no `MyServices` espaço para nome.  Para compilar esse código, uma referência para Microsoft.VisualBasic.DLL deve ser adicionada ao projeto.  
  
 [!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Nem todas as classes na `MyServices` espaço para nome pode ser chamado a partir de um aplicativo do C\#: por exemplo, o <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> classe não é compatível.  Nesse caso específico, os métodos estáticos que fazem parte do <xref:Microsoft.VisualBasic.FileIO.FileSystem>, que também estão contidos no VisualBasic.dll, pode ser usado em vez disso.  Por exemplo, eis como usar um desses métodos para duplicar um diretório:  
  
 [!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Namespaces](../../../csharp/programming-guide/namespaces/index.md)   
 [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)