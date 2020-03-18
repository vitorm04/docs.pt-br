---
title: Tecnologias do .NET Framework não disponíveis no .NET Core
titleSuffix: ''
description: Saiba mais sobre as tecnologias do .NET Framework que não estão disponíveis no .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: bd2488de653ecdfed261100b4c9019bea58fcab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092935"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Tecnologias do .NET Framework não disponíveis no .NET Core

Várias tecnologias disponíveis para bibliotecas .NET Framework não estão disponíveis para uso com o .NET Core, como AppDomains, Remoting, Code Access Security (CAS), Security Transparency e System.EnterpriseServices. Se suas bibliotecas dependerem de uma ou várias dessas tecnologias, considere as abordagens alternativas descritas abaixo. Para obter mais informações sobre compatibilidade com a API, consulte [as alterações de quebra do .NET Core](../compatibility/breaking-changes.md).

Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Procure nos repositórios do GitHub o .NET Core para ver se um problema específico que você encontra é por design. Se você não encontrar tal indicador, faça um problema no [repositório dotnet/runtime](https://github.com/dotnet/runtime/issues) para solicitar APIs e tecnologias específicas. Os problemas que estão portando solicitações são marcados com o rótulo [porta-a-núcleo.](https://github.com/dotnet/runtime/labels/port-to-core)

## <a name="appdomains"></a>AppDomains

Os domínios do aplicativo (AppDomains) isolam os aplicativos uns dos outros. Os AppDomains exigem suporte de runtime e geralmente são muito caros. A criação de domínios adicionais de aplicativos não é suportada e não há planos para adicionar esse recurso no futuro. Para o isolamento de código, use processos separados ou recipientes como uma alternativa. Para carregar dinamicamente <xref:System.Runtime.Loader.AssemblyLoadContext> os conjuntos, use a classe.

Para facilitar a migração do código do .NET Framework, o .NET Core expõe parte da superfície da API <xref:System.AppDomain>. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos que [ `System.AppDomain` ](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) você usa contra a fonte de referência no [repositório GitHub dotnet/runtime](https://github.com/dotnet/runtime). Certifique-se de selecionar o ramo que corresponde à sua versão implementada.

## <a name="remoting"></a>Comunicação remota

A Comunicação Remota do .NET foi identificada como uma arquitetura problemática. Ela é usada para comunicação entre AppDomains, o que não tem mais suporte. Além disso, a Comunicação Remota exige suporte de runtime, o que é caro para manter. Por esses motivos, a Comunicação Remota do .NET não tem suporte no .NET Core, e não planejamos adicionar suporte para ela no futuro.

Para a comunicação entre processos, considere os mecanismos de comunicação interprocesso <xref:System.IO.Pipes> (IPC) como uma alternativa ao Remoting, como a classe ou a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> classe.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), o servidor Web usado pelo ASP.NET Core, é uma opção. Além disso, <xref:System.Net.Sockets> considere usar para cenários de máquinas cruzadas baseadas em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>CAS (segurança de acesso ao código)

A área restrita, que depende do runtime ou da estrutura para restringir quais recursos um aplicativo gerenciado ou uma biblioteca usa ou executa, [não é compatível com o .NET Framework](../../framework/misc/code-access-security.md) e, portanto, também não é compatível com o .NET Core. Há muitos casos no .NET Framework e no runtime em que ocorre uma elevação de privilégios para continuar a tratar a CAS como um limite de segurança. Além disso, a CAS complica mais a implementação e geralmente tem implicações de desempenho de exatidão em aplicativos que não pretendem usá-la.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário, para executar processos com o conjunto mínimo de privilégios.

## <a name="security-transparency"></a>Transparência de Segurança

Assim como a CAS, a Transparência de Segurança separa o código em área restrita do código crítico de segurança de uma forma declarativa, mas [não é mais permitida como um limite de segurança](../../framework/misc/security-transparent-code.md). Esse recurso é amplamente usado pelo Silverlight.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário, para executar processos com o menor conjunto de privilégios.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

O System.EnterpriseServices (COM+) não é compatível com o .NET Core.

## <a name="see-also"></a>Confira também

- [Visão geral da portação do .NET Framework para .NET Core](../porting/index.md)
