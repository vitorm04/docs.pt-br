---
title: Tecnologias do .NET Framework não disponíveis no .NET Core
titleSuffix: ''
description: Saiba mais sobre as tecnologias do .NET Framework que não estão disponíveis no .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: bd2488de653ecdfed261100b4c9019bea58fcab3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092935"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Tecnologias do .NET Framework não disponíveis no .NET Core

Várias tecnologias disponíveis para .NET Framework bibliotecas não estão disponíveis para uso com o .NET Core, como AppDomains, comunicação remota, CAS (segurança de acesso a código), transparência de segurança e System. EnterpriseServices. Se suas bibliotecas dependerem de uma ou várias dessas tecnologias, considere as abordagens alternativas descritas abaixo. Para obter mais informações sobre compatibilidade de API, consulte [alterações significativas no .NET Core](../compatibility/breaking-changes.md).

Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Pesquise os repositórios do GitHub para .NET Core para ver se um problema específico encontrado é por design. Se você não encontrar esse indicador, execute um problema no [repositório dotnet/tempo de execução](https://github.com/dotnet/runtime/issues) para solicitar APIs e tecnologias específicas. Os problemas que são solicitações de portagem são marcados com o rótulo [porta-para-núcleo](https://github.com/dotnet/runtime/labels/port-to-core) .

## <a name="appdomains"></a>AppDomains

Os domínios do aplicativo (AppDomains) isolam os aplicativos uns dos outros. Os AppDomains exigem suporte de runtime e geralmente são muito caros. Não há suporte para a criação de domínios de aplicativo adicionais, e não há planos para adicionar esse recurso no futuro. Para o isolamento de código, use processos ou contêineres separados como alternativa. Para carregar dinamicamente os assemblies, use a classe <xref:System.Runtime.Loader.AssemblyLoadContext>.

Para facilitar a migração do código do .NET Framework, o .NET Core expõe parte da superfície da API <xref:System.AppDomain>. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos que você usa em relação à [origem de referência do`System.AppDomain`](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) no repositório do [GitHub dotnet/tempo de execução](https://github.com/dotnet/runtime). Certifique-se de selecionar a ramificação que corresponde à sua versão implementada.

## <a name="remoting"></a>Comunicação remota

A Comunicação Remota do .NET foi identificada como uma arquitetura problemática. Ela é usada para comunicação entre AppDomains, o que não tem mais suporte. Além disso, a Comunicação Remota exige suporte de runtime, o que é caro para manter. Por esses motivos, a Comunicação Remota do .NET não tem suporte no .NET Core, e não planejamos adicionar suporte para ela no futuro.

Para a comunicação entre processos, considere os mecanismos IPC (comunicação entre processos) como uma alternativa à comunicação remota, como a classe <xref:System.IO.Pipes> ou a classe <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), o servidor Web usado pelo ASP.NET Core, é uma opção. Além disso, considere o uso de <xref:System.Net.Sockets> para cenários de máquina cruzada e em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>CAS (segurança de acesso ao código)

A área restrita, que depende do runtime ou da estrutura para restringir quais recursos um aplicativo gerenciado ou uma biblioteca usa ou executa, [não é compatível com o .NET Framework](../../framework/misc/code-access-security.md) e, portanto, também não é compatível com o .NET Core. Há muitos casos no .NET Framework e no runtime em que ocorre uma elevação de privilégios para continuar a tratar a CAS como um limite de segurança. Além disso, a CAS complica mais a implementação e geralmente tem implicações de desempenho de exatidão em aplicativos que não pretendem usá-la.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário, para executar processos com o conjunto mínimo de privilégios.

## <a name="security-transparency"></a>Transparência de Segurança

Assim como a CAS, a Transparência de Segurança separa o código em área restrita do código crítico de segurança de uma forma declarativa, mas [não é mais permitida como um limite de segurança](../../framework/misc/security-transparent-code.md). Esse recurso é amplamente usado pelo Silverlight.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário, para executar processos com o menor conjunto de privilégios.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

O System.EnterpriseServices (COM+) não é compatível com o .NET Core.

## <a name="see-also"></a>Confira também

- [Visão geral da portabilidade do .NET Framework para o .NET Core](../porting/index.md)
