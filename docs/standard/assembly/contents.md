---
title: Conteúdo do assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d9268b0ec1ea919730a2ebcd209507692284cc6
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973372"
---
# <a name="assembly-contents"></a>Conteúdo do assembly
Em geral, um assembly estático pode consistir em quatro elementos:

- O [manifesto do assembly](manifest.md), que contém metadados do assembly.

- Metadados de tipo.  

- Código MSIL (Microsoft Intermediate Language) que implementa os tipos. Ele é gerado pelo compilador de um ou mais arquivos de código-fonte.

- Um conjunto de recursos.  

Somente o manifesto do assembly é obrigatório, mas tipos e recursos são necessários para atribuir ao assembly uma funcionalidade significativa.

A ilustração a seguir mostra esses elementos agrupados em um único arquivo físico.

![Diagrama que mostra um assembly de arquivo único chamado MyAssembly.dll.](./media/contents/single-file-assembly.gif)

Nesta ilustração, todos os três arquivos pertencem a um assembly, conforme descrito no manifesto de assembly contido em MyAssembly.dll. No sistema de arquivos, eles são três arquivos separados. Observe que o arquivo Util.netmodule foi compilado como um módulo porque não contém informações de assembly. Quando o assembly foi criado, o manifesto do assembly foi adicionado a MyAssembly.dll, indicando seu relacionamento com Util.netmodule e Graphic.bmp.

À medida que cria seu código-fonte, você toma decisões sobre como particionar a funcionalidade do seu aplicativo em um ou mais arquivos. Ao criar código do .NET Framework, você tomará decisões semelhantes sobre como particionar a funcionalidade em um ou mais assemblies.

## <a name="see-also"></a>Consulte também

- [Assemblies no .NET](index.md)
- [Manifesto do assembly](manifest.md)
- [Considerações de segurança do assembly](security-considerations.md)
