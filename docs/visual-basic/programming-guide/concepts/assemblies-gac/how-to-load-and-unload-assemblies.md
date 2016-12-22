---
title: "Como: carregar e descarregar Assemblies (Visual Basic) | Microsoft Docs"
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
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: carregar e descarregar Assemblies (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Os assemblies referenciados pelo seu programa será automaticamente carregados no momento da compilação, mas também é possível carregar assemblies específicos no domínio de aplicativo em tempo de execução. Para obter mais informações, consulte [Como carregar assemblies em um domínio de aplicativo](../Topic/How%20to:%20Load%20Assemblies%20into%20an%20Application%20Domain.md).  
  
 Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm\-lo. Mesmo se o assembly sai do escopo, o arquivo de assembly real permanecerá carregado até que todos os domínios de aplicativo que contenham sejam descarregados.  
  
 Se você quiser descarregar alguns módulos \(assemblies\), mas outros não, considere criando um novo domínio de aplicativo, executar o código dentro desse domínio e, em seguida, o descarregamento desse domínio de aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../Topic/How%20to:%20Unload%20an%20Application%20Domain.md).  
  
### Para carregar um assembly em um domínio de aplicativo  
  
1.  Use um dos vários métodos contidos nas classes de carga <xref:System.AppDomain> e <xref:System.Reflection>. Para obter mais informações, consulte [Como carregar assemblies em um domínio de aplicativo](../Topic/How%20to:%20Load%20Assemblies%20into%20an%20Application%20Domain.md).  
  
### Descarregar um domínio de aplicativo  
  
1.  Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm\-lo. Use o `Unload` método <xref:System.AppDomain> descarregar os domínios de aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../Topic/How%20to:%20Unload%20an%20Application%20Domain.md).  
  
## Consulte também  
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Assemblies e o Cache de Assembly Global \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Como carregar assemblies em um domínio de aplicativo](../Topic/How%20to:%20Load%20Assemblies%20into%20an%20Application%20Domain.md)