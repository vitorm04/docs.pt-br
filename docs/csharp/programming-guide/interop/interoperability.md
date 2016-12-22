---
title: "Interoperabilidade (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Linguagem C#, interoperabilidade"
  - "interoperabilidade COM"
  - "interoperabilidade"
  - "invocação de plataforma, acessando APIs com C#"
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Interoperabilidade (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Interoperabilidade permite que você para preservar e tirar proveito de investimentos existentes em código não gerenciado.  O código executado sob o controle do common language runtime \(CLR\) são chamadas *código gerenciado*, e o código que é executado fora do CLR é chamado *código não gerenciado*.  COM, COM\+, os componentes C\+\+, componentes ActiveX, e Microsoft API do Win32 são exemplos de código não gerenciado.  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] permitem a interoperabilidade com código não gerenciado com os serviços de invocação de plataforma, o namespace de <xref:System.Runtime.InteropServices> , interoperabilidade C\+\+, e interoperabilidade COM \(interoperabilidade COM\).  
  
## Nesta seção  
 [Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Descreve métodos para interoperar entre o código gerenciado C\# e não gerenciados.  
  
 [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C\#](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md)  
 Descreve os recursos que são apresentados no visual C\# 2010 para facilitar a programação do Office.  
  
 [Como usar propriedades indexadas na programação para interoperabilidade COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Descreve como usar propriedades indexadas para acessar as propriedades de que possuem parâmetros.  
  
 [Como usar invocação de plataforma para executar um arquivo wave](../Topic/How%20to:%20Use%20Platform%20Invoke%20to%20Play%20a%20Wave%20File%20\(C%23%20Programming%20Guide\).md)  
 Descreve como usar serviços de invocação de plataforma para reproduzir um arquivo de som.WAV no sistema operacional Windows.  
  
 [Passo a passo: Programação do Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Mostra como criar uma pasta de trabalho do Excel e um documento do word que contém um link para a pasta de trabalho.  
  
 [Exemplo de classe COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Demonstra como expor uma classe C\# como um objeto COM.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=fullName>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Passo a passo: Programação do Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)