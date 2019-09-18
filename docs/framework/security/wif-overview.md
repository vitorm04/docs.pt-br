---
title: Visão geral do Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: c9420ce641da32edc6196be0743d967446a14947
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045002"
---
# <a name="windows-identity-foundation-45-overview"></a>Visão geral do Windows Identity Foundation 4.5
O Windows Identity Foundation 4.5 é um conjunto de classes do .NET Framework para implementar a identidade baseada em declarações em seus aplicativos. Com ele, você obterá mais facilmente os benefícios dos aplicativos e serviços com reconhecimento de declarações. O WIF 4.5 pode ser usado em qualquer aplicativo Web ou serviço Web que usa o .NET Framework versão 4.5 ou posterior. O WIF é apenas uma parte da família de softwares de identidade federada da Microsoft que implementa a visão compartilhada do setor com base em padrões abertos. A identidade federada consiste em três componentes: [Active Directory® serviços de Federação](https://go.microsoft.com/fwlink/?LinkID=247516) (AD FS) 2,0, ACS ( [serviços de controle de acesso) do Windows Azure](https://go.microsoft.com/fwlink/?LinkID=247517) e WIF. Juntos, esses três componentes formam o núcleo da nova plataforma de identidade e acesso na nuvem baseada em declarações da Microsoft.  
  
 Para obter mais informações sobre o WIF, consulte o [site Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=149009) na central de desenvolvedores de segurança no msdn. Para obter uma introdução à criação de aplicativos usando o WIF, consulte [programando o Windows Identity Foundation](https://www.microsoftpressstore.com/store/programming-windows-identity-foundation-9780735627185) por Vittorio Bertocci (publicado pela Microsoft Press).  
  
## <a name="wif-45-features"></a>Recursos do WIF 4.5  
 O WIF 4.5 é um framework para criar aplicativos com reconhecimento de identidade. O framework abstrai os protocolos WS-Trust e WS-Federation e apresenta aos desenvolvedores as APIs para criar aplicativos com reconhecimento de declarações e, se necessário, os serviços de token de segurança (STSs). Os aplicativos podem usar o WIF para processar os tokens emitidos por STSs, como AD FS 2.0 e ACS, e tomam decisões baseadas em identidade no aplicativo Web ou no serviço Web.  
  
 O WIF 4.5 tem os seguintes recursos principais:  
  
- Criar aplicativos com reconhecimento de declarações (usando aplicativos de parceiros confiáveis). O WIF ajuda os desenvolvedores a criar aplicativos com reconhecimento de declarações. Além de fornecer um modelo de declarações, ele fornece aos desenvolvedores de aplicativos um rico conjunto de APIs para ajudar a tomar decisões de acesso do usuário com base em declarações.  O WIF também fornece aos desenvolvedores uma experiência de programação consiste quando eles optam por criar seus aplicativos em ambientes ASP.NET ou WCF.  
  
- Inserir suporte para delegação de identidade em aplicativos com reconhecimento de declarações.  O WIF oferece a capacidade de manter as identidades dos solicitantes originais nos vários limites do serviço. Essa capacidade pode ser atingida usando a funcionalidade "ActAs" ou "OnBehalfOf" no framework, e ela oferece aos desenvolvedores a capacidade de adicionar suporte para delegação de identidade em seus aplicativos com reconhecimento de declarações.  
  
- Cris STSs personalizados.  O WIF facilita substancialmente a criação de um STS personalizado com suporte para o protocolo WS-Trust. Esse STS também é referenciado como STS Ativo.  
  
     Além disso, o framework também fornece suporte para criar um STS que oferece suporte ao protocoloWS-Federation para habilitar clientes de navegador da Web. Esse STS também é referenciado como STS Passivo.  
  
- Nova ferramenta de identidade e acesso para o Visual Studio 11 que permite proteger seu aplicativo com identidade baseada em declarações e aceitar usuários de vários provedores de identidade. Você pode baixar essa ferramenta WIF da seguinte URL: <https://go.microsoft.com/fwlink/?LinkID=245849> ou diretamente no Visual Studio 11 pesquisando por "identidade" diretamente no Gerenciador de extensões. Para saber mais, confira [Ferramenta de Identidade e Acesso para o Visual Studio 2012](identity-and-access-tool-for-vs.md).  
  
 O WIF oferece suporte aos seguintes cenários principais:  
  
- Federação.  O WIF permite habilitar a federação entre dois ou mais parceiros. Seu suporte para criar aplicativos com reconhecimento de declarações (RPs) e STSs personalizados ajuda os desenvolvedores a chegar a esse cenário.  
  
- Delegação de identidade.  O WIF facilita a manutenção das identidades nos limites do serviço para que os desenvolvedores possam chegar a um cenário de delegação de identidade.  
  
- Autenticação de step-up. Os requisitos de autenticação para recursos diferentes em um aplicativo podem variar. O WIF fornece aos desenvolvedores a capacidade de criar aplicativos que podem exigir requisitos de autenticação incrementais (por exemplo: logon inicial com autenticação de nome de usuário/senha e autenticação step-up com cartão inteligente).  
  
 Com o WIF, você obterá mais facilmente os benefícios do modelo de identidade baseado em declarações. Para obter mais informações, leia o [white paper sobre o Windows Identity Foundation para desenvolvedores](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf).
