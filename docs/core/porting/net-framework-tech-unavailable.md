---
title: .NET Framework tecnologias não disponíveis no .NET Core e no .NET 5 +
titleSuffix: ''
description: Saiba mais sobre as tecnologias .NET Framework que não estão disponíveis no .NET Core e no .NET 5,0 e versões posteriores.
author: cartermp
ms.date: 10/13/2020
ms.openlocfilehash: 492aace9db3dc3acef18e995f10b7b5fbe251558
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161030"
---
# <a name="net-framework-technologies-unavailable-on-net-core-and-net-5"></a>.NET Framework tecnologias não disponíveis no .NET Core e no .NET 5 +

Várias tecnologias disponíveis para .NET Framework bibliotecas não estão disponíveis para uso com o .NET Core e o .NET 5,0 e versões posteriores, como domínios de aplicativo, comunicação remota, CAS (segurança de acesso a código), transparência de segurança e <xref:System.EnterpriseServices?displayProperty=fullName> . Se suas bibliotecas dependerem de uma ou mais dessas tecnologias, considere as abordagens alternativas descritas aqui. Para obter mais informações sobre compatibilidade de API, consulte [alterações significativas no .net](../compatibility/breaking-changes.md).

> [!TIP]
> Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Pesquise os repositórios GitHub do .NET para ver se um problema específico encontrado é por design. Se você não encontrar esse indicador, execute um problema no [repositório dotnet/tempo de execução](https://github.com/dotnet/runtime/issues) para solicitar APIs e tecnologias específicas.

## <a name="application-domains"></a>Domínios de aplicativo

Os domínios do aplicativo (AppDomains) isolam os aplicativos uns dos outros. Os AppDomains exigem suporte em tempo de execução e são geralmente caros. Não há suporte para a criação de domínios de aplicativo adicionais, e não há planos para adicionar esse recurso no futuro. Para o isolamento de código, use processos ou contêineres separados como alternativa. Para carregar dinamicamente os assemblies, use a <xref:System.Runtime.Loader.AssemblyLoadContext> classe.

Para tornar a migração de código de .NET Framework mais fácil, o .NET 5 + expõe parte da <xref:System.AppDomain> superfície da API. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos usados em relação à [ `System.AppDomain` origem de referência](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) no [repositório do GitHub dotnet/tempo de execução](https://github.com/dotnet/runtime). Certifique-se de selecionar a ramificação que corresponde à sua versão implementada.

## <a name="remoting"></a>Comunicação remota

A comunicação remota do .NET foi identificada como uma arquitetura problemática. Ele é usado para se comunicar entre domínios de aplicativo, que não têm mais suporte. Além disso, a comunicação remota requer suporte a tempo de execução, o que é caro para manter. Por esses motivos, o .NET Remoting não tem suporte no .NET Core e no .NET 5 +, e não planejamos adicionar suporte para ele no futuro.

Para a comunicação entre processos, considere os mecanismos IPC (comunicação entre processos) como uma alternativa à comunicação remota, como a <xref:System.IO.Pipes> classe ou a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> classe.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](/aspnet/core/fundamentals/servers/kestrel), que é o servidor Web usado pelo ASP.NET Core, é uma opção aqui. Além disso, considere o uso <xref:System.Net.Sockets> de cenários de máquina cruzada e baseados em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>CAS (Segurança de Acesso do Código)

A área restrita, que se baseia no tempo de execução ou na estrutura para restringir quais recursos um aplicativo ou uma biblioteca gerenciada usa ou executa, [não tem suporte no .NET Framework](../../framework/misc/code-access-security.md) e, portanto, também não tem suporte no .NET Core e no .NET 5 +. Há muitos casos no .NET Framework e no runtime em que ocorre uma elevação de privilégios para continuar a tratar a CAS como um limite de segurança. Além disso, a CAS complica mais a implementação e geralmente tem implicações de desempenho de exatidão em aplicativos que não pretendem usá-la.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário, para executar processos com o conjunto mínimo de privilégios.

## <a name="security-transparency"></a>Transparência de segurança

Semelhante ao CAS, a transparência de segurança separa o código em área restrita do código crítico de segurança de maneira declarativa, mas [não tem mais suporte como um limite de segurança](../../framework/misc/security-transparent-code.md). Esse recurso é amplamente usado pelo Silverlight.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário, para executar processos com o menor conjunto de privilégios.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

<xref:System.EnterpriseServices?displayProperty=fullName> (COM+) não tem suporte no .NET Core e no .NET 5 +.

## <a name="see-also"></a>Veja também

- [Visão geral da portabilidade do .NET Framework para o .NET Core](index.md)
