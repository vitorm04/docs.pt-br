---
title: "Como: carregar e descarregar Assemblies (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: carregar e descarregar Assemblies (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Os assemblies referenciados pelo seu programa será automaticamente carregados no momento da compilação, mas também é possível carregar assemblies específicos no domínio de aplicativo em tempo de execução. Para obter mais informações, consulte [Como carregar assemblies em um domínio de aplicativo](../Topic/How%20to:%20Load%20Assemblies%20into%20an%20Application%20Domain.md).  
  
 Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm\-lo. Mesmo se o assembly sai do escopo, o arquivo de assembly real permanecerá carregado até que todos os domínios de aplicativo que contenham sejam descarregados.  
  
 Se você quiser descarregar alguns módulos \(assemblies\), mas outros não, considere criando um novo domínio de aplicativo, executar o código dentro desse domínio e, em seguida, o descarregamento desse domínio de aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../Topic/How%20to:%20Unload%20an%20Application%20Domain.md).  
  
### Para carregar um assembly em um domínio de aplicativo  
  
1.  Use um dos vários métodos contidos nas classes de carga <xref:System.AppDomain> e <xref:System.Reflection>. Para obter mais informações, consulte [Como carregar assemblies em um domínio de aplicativo](../Topic/How%20to:%20Load%20Assemblies%20into%20an%20Application%20Domain.md).  
  
### Descarregar um domínio de aplicativo  
  
1.  Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm\-lo. Use o `Unload` método <xref:System.AppDomain> descarregar os domínios de aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../Topic/How%20to:%20Unload%20an%20Application%20Domain.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Assemblies e o Cache de Assembly Global \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/assemblies-and-the-global-assembly-cache.md)   
 [Como carregar assemblies em um domínio de aplicativo](../Topic/How%20to:%20Load%20Assemblies%20into%20an%20Application%20Domain.md)