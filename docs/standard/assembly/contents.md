---
title: Conteúdos do assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345569"
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

## <a name="see-also"></a>Veja também

- [Assemblies no .NET](index.md)
- [Manifesto do assembly](manifest.md)
- [Considerações de segurança do assembly](security-considerations.md)
