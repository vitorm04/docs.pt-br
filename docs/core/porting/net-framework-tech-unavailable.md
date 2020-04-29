---
title: Tecnologias do .NET Framework não disponíveis no .NET Core
titleSuffix: ''
description: Saiba mais sobre as tecnologias do .NET Framework que não estão disponíveis no .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: f95205330837551085b8f58dfbdfcd702356c98f
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506824"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Tecnologias do .NET Framework não disponíveis no .NET Core

Várias tecnologias disponíveis para .NET Framework bibliotecas não estão disponíveis para uso com o .NET Core, como AppDomains, comunicação remota, CAS (segurança de acesso a código), transparência de segurança e System. EnterpriseServices. Se suas bibliotecas dependerem de uma ou várias dessas tecnologias, considere as abordagens alternativas descritas abaixo. Para obter mais informações sobre compatibilidade de API, consulte [alterações significativas no .NET Core](../compatibility/breaking-changes.md).

Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Pesquise os repositórios do GitHub para .NET Core para ver se um problema específico encontrado é por design. Se você não encontrar esse indicador, execute um problema no [repositório dotnet/tempo de execução](https://github.com/dotnet/runtime/issues) para solicitar APIs e tecnologias específicas.

## <a name="appdomains"></a>AppDomains

Os domínios do aplicativo (AppDomains) isolam os aplicativos uns dos outros. Os AppDomains exigem suporte em tempo de execução e são geralmente caros. Não há suporte para a criação de domínios de aplicativo adicionais, e não há planos para adicionar esse recurso no futuro. Para o isolamento de código, use processos ou contêineres separados como alternativa. Para carregar dinamicamente os assemblies, use <xref:System.Runtime.Loader.AssemblyLoadContext> a classe.

Para facilitar a migração do código do .NET Framework, o .NET Core expõe parte da superfície da API <xref:System.AppDomain>. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos usados em relação à [ `System.AppDomain` origem de referência](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) no [repositório do GitHub dotnet/tempo de execução](https://github.com/dotnet/runtime). Certifique-se de selecionar a ramificação que corresponde à sua versão implementada.

## <a name="remoting"></a>Comunicação remota

A Comunicação Remota do .NET foi identificada como uma arquitetura problemática. Ela é usada para comunicação entre AppDomains, o que não tem mais suporte. Além disso, a Comunicação Remota exige suporte de runtime, o que é caro para manter. Por esses motivos, a Comunicação Remota do .NET não tem suporte no .NET Core, e não planejamos adicionar suporte para ela no futuro.

Para a comunicação entre processos, considere os mecanismos IPC (comunicação entre processos) como uma alternativa à comunicação remota, como <xref:System.IO.Pipes> a classe ou <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> a classe.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](/aspnet/core/fundamentals/servers/kestrel), o servidor Web usado pelo ASP.NET Core, é uma opção. Além disso, considere <xref:System.Net.Sockets> o uso de cenários de máquina cruzada e baseados em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

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
