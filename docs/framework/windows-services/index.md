---
title: "Desenvolvendo aplicativos do Serviço Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a>Desenvolvendo aplicativos do Serviço Windows
Usando o Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou o Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, você pode criar serviços facilmente, criando um aplicativo que é instalado como um serviço. Esse tipo de aplicativo é chamado um serviço do Windows. Com recursos de estrutura, você pode criar serviços, instalá-los, iniciar, interromper e controlar seu comportamento.  
  
> [!WARNING]
>  O modelo de serviço do Windows para C++ não foi incluído no Visual Studio 2010. Para criar um serviço do Windows, você pode criar um serviço em código gerenciado em Visual c# ou Visual Basic, que pode interagir com o código C++ existente se necessário, ou você pode criar um serviço do Windows em C++ nativo usando o [Assistente de projeto de ATL](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Fornece uma visão geral de aplicativos de serviço do Windows, o tempo de vida de um serviço e como aplicativos de serviço diferem de outros tipos de projeto comum.  
  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Fornece um exemplo de criação de um serviço no [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e Visual c#.  
  
 [Arquitetura de programação de aplicativo de serviço](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Explica os elementos de linguagem usados em programação de serviço.  
  
 [Como criar Serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Descreve o processo de criação e configuração de serviços do Windows usando o modelo de projeto de serviço do Windows.  
  
## <a name="related-sections"></a>Seções relacionadas  
 <xref:System.ServiceProcess.ServiceBase>  
 Descreve os principais recursos da <xref:System.ServiceProcess.ServiceBase> classe, que é usada para criar serviços.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Descreve os recursos do <xref:System.ServiceProcess.ServiceProcessInstaller> classe, que é usada junto com o <xref:System.ServiceProcess.ServiceInstaller> classe para instalar e desinstalar seus serviços.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Descreve os recursos do <xref:System.ServiceProcess.ServiceInstaller> classe, que é usada junto com o <xref:System.ServiceProcess.ServiceProcessInstaller> classe para instalar e desinstalar o serviço.  
  
 [NIB criar projetos de modelos](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Descreve os projetos de tipos usados neste capítulo e como escolher entre eles.
