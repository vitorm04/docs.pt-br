---
title: Carregamento de dependência - .NET Core
description: Visão geral do carregamento de dependência gerenciado e não gerenciado no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416683"
---
# <a name="dependency-loading-in-net-core"></a>Carregamento de dependência no Núcleo .NET

Cada aplicativo .NET Core tem dependências. Mesmo o `hello world` aplicativo simples tem dependências de partes das bibliotecas de classe .NET Core.

Entender a lógica de carregamento padrão do grupo .NET Core pode ajudar a entender e depurar problemas típicos de implantação.

Em alguns aplicativos, as dependências são determinadas dinamicamente em tempo de execução. Nessas situações, é fundamental entender como montagens gerenciadas e dependências não gerenciadas são carregadas.

## <a name="understanding-assemblyloadcontext"></a>Entendendo o AssemblyLoadContext

A <xref:System.Runtime.Loader.AssemblyLoadContext> API é central para o projeto de carregamento .NET Core. O artigo [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) fornece uma visão geral conceitual do projeto.

## <a name="loading-details"></a>Carregando detalhes

Os detalhes do algoritmo de carregamento são cobertos brevemente em vários artigos:

- [Algoritmo de carregamento de montagem gerenciado](loading-managed.md)
- [Algoritmo de carregamento de montagem por satélite](loading-resources.md)
- [Algoritmo de carregamento de biblioteca não gerenciado (nativo)](loading-unmanaged.md)
- [Sondagem padrão](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Criar um aplicativo do .NET Core com plug-ins

O tutorial [Criar um aplicativo .NET Core com plugins](../tutorials/creating-app-with-plugin-support.md) descreve como criar um AssemblyLoadContext personalizado. Ele usa <xref:System.Runtime.Loader.AssemblyDependencyResolver> um para resolver as dependências do plugin. O tutorial isola corretamente as dependências do plugin do aplicativo de hospedagem.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Como usar e depurar a capacidade de descarregamento de assembly no .NET Core

A [capacidade de descarga de montagem de Como usar e depurar no](../../standard/assembly/unloadability.md) artigo .NET Core é um tutorial passo-a-passo. Ele mostra como carregar um aplicativo .NET Core, executá-lo e, em seguida, descarregá-lo. O artigo também fornece dicas de depuração.
