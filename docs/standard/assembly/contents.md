---
title: Conteúdos do assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75345569"
---
# <a name="assembly-contents"></a>Conteúdos do assembly

Em geral, um assembly estático pode consistir em quatro elementos:

- O [manifesto do assembly](manifest.md), que contém metadados do assembly.

- Metadados de tipo.  

- Código MSIL (Microsoft Intermediate Language) que implementa os tipos. Ele é gerado pelo compilador a partir de um ou mais arquivos de código fonte.

- Um conjunto de [recursos.](../../framework/resources/index.md)  

Somente o manifesto do assembly é obrigatório, mas tipos e recursos são necessários para atribuir ao assembly uma funcionalidade significativa.

A ilustração a seguir mostra esses elementos agrupados em um único arquivo físico:

![Um conjunto de arquivos únicos chamado MyAssembly.dll](./media/contents/single-file-assembly.gif)

Ao projetar seu código-fonte, você tome decisões explícitas sobre como dividir a funcionalidade do seu aplicativo em um ou mais arquivos. Ao projetar o código .NET, você tomará decisões semelhantes sobre como dividir a funcionalidade em um ou mais conjuntos.

## <a name="see-also"></a>Confira também

- [Assemblies no .NET](index.md)
- [Manifesto de assembléia](manifest.md)
- [Considerações sobre a segurança do assembly](security-considerations.md)
