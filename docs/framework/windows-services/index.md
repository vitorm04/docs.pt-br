---
title: Desenvolvendo aplicativos do Serviço Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: af6e4bf7697b3139f6809295737fdd0d90b7f013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="developing-windows-service-applications"></a>Desenvolvendo aplicativos do Serviço Windows
Usando o Microsoft Visual Studio ou o SDK do Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], você pode criar serviços facilmente criando um aplicativo que é instalado como um serviço. Esse tipo de aplicativo é chamado de um serviço Windows. Com recursos de estrutura, você pode criar serviços, instalá-los, iniciar, interromper e controlar seu comportamento.  
  
> [!WARNING]
>  O modelo de serviço Windows para C++ não foi incluído no Visual Studio 2010. Para criar um serviço Windows, você pode criar um serviço em código gerenciado no Visual C# ou Visual Basic, que pode interagir com o código C++ existente, se necessário, ou pode criar um serviço Windows em C++ nativo usando o [Assistente de Projeto de ATL](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Fornece uma visão geral de aplicativos de serviço Windows, o tempo de vida de um serviço e como aplicativos de serviço diferem de outros tipos de projeto comum.  
  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Fornece um exemplo de como criar um serviço no Visual Basic e Visual C#.  
  
 [Arquitetura de programação de aplicativo de serviço](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Explica os elementos de linguagem usados na programação de serviço.  
  
 [Como criar Serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Descreve o processo de criação e configuração de serviços Windows usando o modelo de projeto de serviço Windows.  
  
## <a name="related-sections"></a>Seções relacionadas  
 <xref:System.ServiceProcess.ServiceBase>  
 Descreve os principais recursos da classe <xref:System.ServiceProcess.ServiceBase>, que é usada para criar serviços.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Descreve os recursos da classe <xref:System.ServiceProcess.ServiceProcessInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceInstaller> para instalar e desinstalar serviços.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Descreve os recursos da classe <xref:System.ServiceProcess.ServiceInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceProcessInstaller> para instalar e desinstalar o serviço.  
  
 [NIB Criando projetos com base em modelos](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Descreve os tipos de projeto usados neste capítulo e como escolher entre eles.
