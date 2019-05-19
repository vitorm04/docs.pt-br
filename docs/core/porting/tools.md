---
title: Ferramentas de portabilidade para o .NET Core
description: Conheça algumas das ferramentas que você pode usar para portar para o .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: d0b74b5708f31922b72fa0e236c8bbe69ae06217
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632247"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Ferramentas para ajudar com a portabilidade para o .NET Core

As ferramentas listadas neste artigo podem ser úteis para portar:

* [Analisador de Portabilidade do .NET](../../standard/analyzers/portability-analyzer.md), uma cadeia de ferramentas que pode gerar um relatório sobre o grau de portabilidade do código entre o .NET Framework e .NET Core:  Como uma [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) Como uma [extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
* [Analisador de API do .NET](../../standard/analyzers/api-analyzer.md) – um analisador Roslyn que descobre possíveis riscos de compatibilidade para APIs C# em diferentes plataformas e detecta chamadas a APIs preteridas.

Além disso, você pode tentar fazer a portabilidade de soluções menores ou projetos individuais para o formato de arquivo de projeto do .NET Core com a ferramenta [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).

> [!WARNING] 
> CsprojToVs2017 é uma ferramenta de terceiros. Não há nenhuma garantia de que ela funcionará para todos os seus projetos, e isso pode causar alterações sutis no comportamento que dependem de você. CsprojToVs2017 deve ser usada como um _ponto de partida_ que automatize as funções básicas que podem ser automatizadas. Não é uma solução garantida para a migração de formatos de arquivo de projeto.
