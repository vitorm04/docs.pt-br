---
title: Conteúdo de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1334f8c8e1b5898e93697461f609429d4aae764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921696"
---
# <a name="assembly-contents"></a>Conteúdo de um assembly
Em geral, um assembly estático pode consistir em quatro elementos:  
  
- O [manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md), que contém metadados do assembly.  
  
- Metadados de tipo.  
  
- Código MSIL (Microsoft Intermediate Language) que implementa os tipos.  
  
- Um conjunto de recursos.  
  
 Somente o manifesto do assembly é obrigatório, mas tipos e recursos são necessários para atribuir ao assembly uma funcionalidade significativa.  
  
 Há várias maneiras de se agrupar esses elementos em um assembly. Você pode agrupar todos os elementos em um único arquivo físico, mostrado na ilustração a seguir.  
  
 ![Diagrama que mostra um assembly de arquivo único chamado MyAssembly.dll.](./media/assembly-contents/single-file-assembly.gif)  
  
 Como alternativa, os elementos de um assembly podem estar contidos em vários arquivos. Esses arquivos podem ser módulos de código compilado (.netmodule), recursos (como arquivos .bmp ou .jpg) ou outros arquivos exigidos pelo aplicativo. Crie um assembly de vários arquivos quando quiser combinar módulos escritos em diferentes linguagens e otimizar o download de um aplicativo colocando tipos pouco usados em um módulo baixado apenas quando necessário.  
  
 Na ilustração a seguir, o desenvolvedor de um aplicativo hipotético optou por separar alguns códigos de utilitários em um módulo diferente e manter um arquivo de recurso grande (neste caso, uma imagem .bmp) em seu arquivo original. O .NET Framework só baixa um arquivo quando ele é referenciado; manter códigos pouco referenciados em um arquivo separado do aplicativo otimiza o download do código.  
  
 ![Diagrama que mostra um assembly de vários arquivos.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
> Os arquivos que compõem um assembly de vários arquivos não estão fisicamente vinculados pelo sistema de arquivos. Em vez disso, eles estão vinculados por meio do manifesto de assembly, e o Common Language Runtime os gerencia como uma unidade.  
  
 Nesta ilustração, todos os três arquivos pertencem a um assembly, conforme descrito no manifesto de assembly contido em MyAssembly.dll. No sistema de arquivos, eles são três arquivos separados. Observe que o arquivo Util.netmodule foi compilado como um módulo porque não contém informações de assembly. Quando o assembly foi criado, o manifesto do assembly foi adicionado a MyAssembly.dll, indicando seu relacionamento com Util.netmodule e Graphic.bmp.  
  
 À medida que cria seu código-fonte, você toma decisões sobre como particionar a funcionalidade do seu aplicativo em um ou mais arquivos. Ao criar código do .NET Framework, você tomará decisões semelhantes sobre como particionar a funcionalidade em um ou mais assemblies.  
  
## <a name="see-also"></a>Consulte também

- [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md)
- [Considerações sobre segurança de assembly](../../../docs/framework/app-domains/assembly-security-considerations.md)
