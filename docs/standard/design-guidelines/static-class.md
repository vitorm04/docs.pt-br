---
title: Design de classe estática
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743599"
---
# <a name="static-class-design"></a>Design de classe estática
Uma classe estática é definida como uma classe que contém somente membros estáticos (é claro que, além dos membros da instância herdados de <xref:System.Object?displayProperty=nameWithType> e possivelmente um Construtor privado). Algumas linguagens fornecem suporte interno para classes estáticas. No C# 2,0 e posterior, quando uma classe é declarada como estática, ela é sealed, abstract e nenhum membro de instância pode ser substituído ou declarado.

 As classes estáticas são um compromisso entre o design puro orientado a objeto e a simplicidade. Normalmente, eles são usados para fornecer atalhos para outras operações (como <xref:System.IO.File?displayProperty=nameWithType>), os proprietários de métodos de extensão ou a funcionalidade para a qual um wrapper completo orientado a objeto não é garantido (como <xref:System.Environment?displayProperty=nameWithType>).

 ✔️ usar classes estáticas com moderação.

 Classes estáticas devem ser usadas somente como classes de suporte para o núcleo orientado a objeto da estrutura.

 ❌ não tratar classes estáticas como um Bucket variado.

 ❌ não declare nem substitui membros de instância em classes estáticas.

 ✔️ declare classes estáticas como lacradas, abstratas e adicione um construtor de instância privada se a linguagem de programação não tiver suporte interno para classes estáticas.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
