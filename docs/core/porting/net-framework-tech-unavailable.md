---
title: Tecnologias do .NET Framework não disponíveis no .NET Core
description: Saiba mais sobre as tecnologias do .NET Framework que não estão disponíveis no .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 6c457812f04b8e6503e5162b9f1f6497e7ef83b1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343563"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Tecnologias do .NET Framework não disponíveis no .NET Core

Várias tecnologias disponíveis para .NET Framework bibliotecas não estão disponíveis para uso com o .NET Core, como AppDomains, comunicação remota, CAS (segurança de acesso a código), transparência de segurança e System. EnterpriseServices. Se suas bibliotecas dependerem de uma ou várias dessas tecnologias, considere as abordagens alternativas descritas abaixo. Para obter mais informações sobre compatibilidade de API, consulte [alterações significativas no .NET Core](../compatibility/breaking-changes.md).

Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Primeiro, você deve pesquisar os repositórios do GitHub para .NET Core para ver se um determinado problema encontrado é por design. Se você não encontrar um indicador desse tipo, registre um problema nos [problemas do repositório dotnet/corefx](https://github.com/dotnet/corefx/issues) no GitHub para solicitar APIs e tecnologias específicas. [As solicitações de portabilidade nos problemas](https://github.com/dotnet/corefx/labels/port-to-core) são marcadas com o rótulo `port-to-core`.

## <a name="appdomains"></a>AppDomains

Os domínios do aplicativo (AppDomains) isolam os aplicativos uns dos outros. Os AppDomains exigem suporte de runtime e geralmente são muito caros. Não há suporte para a criação de domínios de aplicativo adicionais, e não há planos para adicionar esse recurso no futuro. Para o isolamento de código, use processos ou contêineres separados como alternativa. Para o carregamento dinâmico de assemblies, use a classe <xref:System.Runtime.Loader.AssemblyLoadContext>.

Para facilitar a migração do código do .NET Framework, o .NET Core expõe parte da superfície da API <xref:System.AppDomain>. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos que você usa na [fonte de referência de `System.AppDomain`](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) no [repositório dotnet/corefx do GitHub](https://github.com/dotnet/corefx) selecionando o branch que corresponde à versão implementada.

## <a name="remoting"></a>Comunicação Remota

A Comunicação Remota do .NET foi identificada como uma arquitetura problemática. Ela é usada para comunicação entre AppDomains, o que não tem mais suporte. Além disso, a Comunicação Remota exige suporte de runtime, o que é caro para manter. Por esses motivos, a Comunicação Remota do .NET não tem suporte no .NET Core, e não planejamos adicionar suporte para ela no futuro.

Para a comunicação entre processos, considere os mecanismos IPC (comunicação entre processos) como uma alternativa à comunicação remota, como a classe <xref:System.IO.Pipes> ou a classe <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), o servidor Web usado pelo ASP.NET Core, é uma opção. Além disso, considere o uso de <xref:System.Net.Sockets> para cenários de máquina cruzada e em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>CAS (Segurança de Acesso do Código)

A área restrita, que depende do runtime ou da estrutura para restringir quais recursos um aplicativo gerenciado ou uma biblioteca usa ou executa, [não é compatível com o .NET Framework](../../framework/misc/code-access-security.md) e, portanto, também não é compatível com o .NET Core. Há muitos casos no .NET Framework e no runtime em que ocorre uma elevação de privilégios para continuar a tratar a CAS como um limite de segurança. Além disso, a CAS complica mais a implementação e geralmente tem implicações de desempenho de exatidão em aplicativos que não pretendem usá-la.

Use os limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário para executar processos com o conjunto mínimo de privilégios.

## <a name="security-transparency"></a>Transparência de Segurança

Assim como a CAS, a Transparência de Segurança separa o código em área restrita do código crítico de segurança de uma forma declarativa, mas [não é mais permitida como um limite de segurança](../../framework/misc/security-transparent-code.md). Esse recurso é amplamente usado pelo Silverlight.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário para executar processos com o conjunto mínimo de privilégios.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

O System.EnterpriseServices (COM+) não é compatível com o .NET Core.

>[!div class="step-by-step"]
>[Avançar](third-party-deps.md)
