---
title: "Como implantar aplicativos .NET existentes para o serviço de aplicativo do Azure"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Como implantar aplicativos .NET existentes para o serviço de aplicativo do Azure"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aefcd79574cbbf6b3759bfa6cc0f9e46a58244ce
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>Como implantar aplicativos .NET existentes para o serviço de aplicativo do Azure 

O recurso de aplicativos Web do serviço de aplicativo do Azure é uma plataforma de computação totalmente gerenciado que é otimizada para hospedar aplicativos web e sites. Esta oferta de PaaS no Microsoft Azure permite você se concentre em sua lógica de negócios, enquanto o Azure se encarrega da infraestrutura para executar e dimensionar seus aplicativos.

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>Validar sites e migrar para o serviço de aplicativo com o Assistente de migração do serviço de aplicativo do Azure

Quando você cria um novo aplicativo no Visual Studio, mover o aplicativo de serviço de aplicativo normalmente é simples. No entanto, se você planeja migrar um aplicativo existente para o serviço de aplicativo, primeiro você precisa avaliar se todas as dependências do aplicativo são compatíveis com o serviço de aplicativo. Isso inclui dependências, como servidor de sistema operacional e qualquer software de terceiros que está instalado no servidor.

Você pode usar [Assistente de migração do serviço de aplicativo do Azure](https://www.migratetoazure.net/) para analisar os sites e, em seguida, migrá-los de servidores de web do Windows e Linux para o serviço de aplicativo. Como parte da migração, a ferramenta cria aplicativos web e bancos de dados no Azure conforme necessário, publica o conteúdo e publica seu banco de dados.

Azure aplicativo serviço Assistente de migração dá suporte à migração do IIS em execução no Windows Server para a nuvem. Serviço de aplicativo oferece suporte ao Windows Server 2003 e versões posteriores.

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> **Figura 4-5.** Usando o Assistente de migração do serviço de aplicativo do Azure

Assistente de migração do serviço de aplicativo é uma ferramenta que move os sites de seus servidores web na nuvem do Azure.

Depois que um site é migrado para o serviço de aplicativo, o site tem tudo o que precisa para executar com segurança e eficiência. Sites são configurados e executados automaticamente no serviço em nuvem do Azure PaaS (serviço de aplicativo).

A ferramenta de migração do serviço de aplicativo pode analisar seus sites e relatar sobre sua compatibilidade para mover para o serviço de aplicativo. Se você estiver satisfeito com a análise, você pode deixar Assistente de migração do serviço de aplicativo migrar conteúdo, dados e as configurações para você. Se um site não é totalmente compatível, a ferramenta de migração informa o que você precisa ajustar para que funcione corretamente.

### <a name="additional-resources"></a>Recursos adicionais

- **Assistente de migração do serviço de aplicativo do Azure**

    [https://www.migratetoazure.net/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[Anterior](what-about-cloud-optimized-applications.md)
[Próximo](deploy-existing-net-apps-as-windows-containers.md)
