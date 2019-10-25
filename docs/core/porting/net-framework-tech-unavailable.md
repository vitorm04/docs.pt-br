---
title: Tecnologias do .NET Framework não disponíveis no .NET Core
description: Saiba mais sobre as tecnologias do .NET Framework que não estão disponíveis no .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: e5626d7b3e402848e2e84c49d4e98e109f62982d
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846810"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Tecnologias do .NET Framework não disponíveis no .NET Core

Várias tecnologias disponíveis para as bibliotecas do .NET Framework não estão disponíveis para uso com o .NET Core, como AppDomains, Comunicação Remota, CAS (Segurança de acesso do código) e Transparência de segurança. Se suas bibliotecas dependerem de uma ou várias dessas tecnologias, considere as abordagens alternativas descritas abaixo. Para obter mais informações sobre compatibilidade de API, consulte o artigo [alterações significativas do .NET Core](../compatibility/breaking-changes.md) .

Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Primeiro você deve pesquisar o .NET Core nos repositórios do GitHub para saber se um problema específico encontrado está relacionado ao design, mas se não encontrar esse tipo de indicação, envie um problema em [problemas no repositório dotnet/corefx](https://github.com/dotnet/corefx/issues) no GitHub para solicitar APIs e tecnologias específicas. [As solicitações de portabilidade nos problemas](https://github.com/dotnet/corefx/labels/port-to-core) são marcadas com o rótulo `port-to-core`.

## <a name="appdomains"></a>AppDomains

Os domínios do aplicativo (AppDomains) isolam os aplicativos uns dos outros. Os AppDomains exigem suporte de tempo de execução e geralmente são muito caros. Não há suporte para a criação de domínios do aplicativo adicionais. Não pretendemos adicionar esse recurso no futuro. Para isolamento de código, recomendamos como alternativa o uso de processos separados ou contêineres. Para o carregamento dinâmico de assemblies, recomendamos a nova classe <xref:System.Runtime.Loader.AssemblyLoadContext>.

Para facilitar a migração do código do .NET Framework, o .NET Core expõe parte da superfície da API <xref:System.AppDomain>. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos que você usa na [fonte de referência de `System.AppDomain`](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) no [repositório dotnet/corefx do GitHub](https://github.com/dotnet/corefx) selecionando o branch que corresponde à versão implementada.

## <a name="remoting"></a>Comunicação Remota

A Comunicação Remota do .NET foi identificada como uma arquitetura problemática. Ela é usada para comunicação entre AppDomains, o que não tem mais suporte. Além disso, a Comunicação Remota exige suporte de tempo de execução, o que é caro para manter. Por esses motivos, a Comunicação Remota do .NET não tem suporte no .NET Core, e não planejamos adicionar suporte para ela no futuro.

Para comunicação entre processos, considere mecanismos IPC (comunicação entre processos) como uma alternativa à Comunicação Remota, tais como a classe <xref:System.IO.Pipes> ou <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), o servidor Web usado pelo ASP.NET Core, é uma opção. Considere também o uso de <xref:System.Net.Sockets> para cenários entre computadores baseados em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>CAS (Segurança de Acesso do Código)

A área restrita, que depende do tempo de execução ou da estrutura para restringir quais recursos um aplicativo gerenciado ou uma biblioteca usa ou executa, [não é compatível com o .NET Framework](../../framework/misc/code-access-security.md) e, portanto, também não é compatível com o .NET Core. Há muitos casos no .NET Framework e no tempo de execução em que ocorre uma elevação de privilégios para continuar a tratar a CAS como um limite de segurança. Além disso, a CAS complica mais a implementação e geralmente tem implicações de desempenho de exatidão em aplicativos que não pretendem usá-la.

Use os limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário para executar processos com o conjunto mínimo de privilégios.

## <a name="security-transparency"></a>Transparência de Segurança

Assim como a CAS, a Transparência de Segurança separa o código em área restrita do código crítico de segurança de uma forma declarativa, mas [não é mais permitida como um limite de segurança](../../framework/misc/security-transparent-code.md). Esse recurso é amplamente usado pelo Silverlight. 

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário para executar processos com o conjunto mínimo de privilégios.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

O System.EnterpriseServices (COM+) não é compatível com o .NET Core.

>[!div class="step-by-step"]
>[Avançar](third-party-deps.md)
