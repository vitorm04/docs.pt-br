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
ms.openlocfilehash: 79de8adbc0f994653f308882b335da2ffa5f7455
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035916"
---
# <a name="develop-windows-service-apps"></a>Desenvolver aplicativos de serviço Windows

Usando o Visual Studio ou o SDK do .NET Framework, você pode criar serviços facilmente criando um aplicativo que é instalado como um serviço. Esse tipo de aplicativo é chamado de um serviço Windows. Com recursos de estrutura, você pode criar serviços, instalá-los, iniciar, interromper e controlar seu comportamento.

> [!NOTE]
> No Visual Studio, você pode criar um serviço em código gerenciado em Visual C# ou Visual Basic, que podem interoperar com o código C++ existente se necessário. Ou você pode criar um serviço Windows em C++ nativo usando o [Assistente de Projeto ATL](/cpp/atl/reference/atl-project-wizard).

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

<xref:System.ServiceProcess.ServiceBase> – Descreve os principais recursos da classe <xref:System.ServiceProcess.ServiceBase>, que é usada para criar serviços.

<xref:System.ServiceProcess.ServiceProcessInstaller> – Descreve os recursos da classe <xref:System.ServiceProcess.ServiceProcessInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceInstaller> para instalar e desinstalar o serviço.

<xref:System.ServiceProcess.ServiceInstaller> – Descreve os recursos da classe <xref:System.ServiceProcess.ServiceInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceProcessInstaller> para instalar e desinstalar seu serviço.

[Criar projetos de modelos](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) – descreve os projetos de tipos usados neste capítulo e como escolher entre eles.
