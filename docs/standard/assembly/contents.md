---
title: Conteúdos do assembly
description: Este artigo descreve o conteúdo de um assembly .NET, que pode incluir metadados de assembly, tipos de metadados, código MSIL e recursos.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 94df452162ed7290fab7fa267d2624e6d844a587
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378562"
---
# <a name="assembly-contents"></a>Conteúdos do assembly

Em geral, um assembly estático pode consistir em quatro elementos:

- O [manifesto do assembly](manifest.md), que contém metadados do assembly.

- Metadados de tipo.  

- Código MSIL (Microsoft Intermediate Language) que implementa os tipos. Ele é gerado pelo compilador de um ou mais arquivos de código-fonte.

- Um conjunto de [recursos](../../framework/resources/index.md).  

Somente o manifesto do assembly é obrigatório, mas tipos e recursos são necessários para atribuir ao assembly uma funcionalidade significativa.

A ilustração a seguir mostra esses elementos agrupados em um único arquivo físico:

![Um assembly de arquivo único chamado MyAssembly. dll](./media/contents/single-file-assembly.gif)

Ao projetar seu código-fonte, você toma decisões explícitas sobre como particionar a funcionalidade do seu aplicativo em um ou mais arquivos. Ao criar o código .NET, você tomará decisões semelhantes sobre como particionar a funcionalidade em um ou mais assemblies.

## <a name="see-also"></a>Confira também

- [Assemblies no .NET](index.md)
- [Manifesto do assembly](manifest.md)
- [Considerações sobre a segurança do assembly](security-considerations.md)
