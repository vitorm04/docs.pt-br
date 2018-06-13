---
title: Design de interface
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dea5877f952869d5c84d6019617fcdc52d8ee0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573033"
---
# <a name="interface-design"></a>Design de interface
Embora a maioria das APIs melhor são modelados usando classes e estruturas, há casos em que as interfaces são mais apropriados ou são a única opção.  
  
 O CLR não suporta herança múltipla (ou seja, classes CLR não podem herdar de mais de uma classe base), mas permite tipos implementar uma ou mais interfaces além de herdar de uma classe base. Portanto, as interfaces geralmente são usadas para obter o efeito de várias heranças. Por exemplo, <xref:System.IDisposable> é uma interface que permite tipos dar suporte a disposability independente de qualquer outra hierarquia de herança no qual deseja participar.  
  
 A outra situação em que define uma interface é apropriada está na criação de uma interface comum que pode ser compatível com vários tipos, incluindo alguns tipos de valor. Tipos de valor não podem herdar de tipos diferentes de <xref:System.ValueType>, mas elas podem implementar interfaces, portanto, usar uma interface é a única opção para fornecer um tipo de base comum.  
  
 **FAZER ✓** definir uma interface, se você precisar de algum API comuns para serem suportados por um conjunto de tipos que inclui os tipos de valor.  
  
 **✓ CONSIDERE** define uma interface, se você precisar oferecer suporte a sua funcionalidade em tipos que herdam já algum outro tipo.  
  
 **X Evite** usando as interfaces do marcador (interfaces com nenhum membro).  
  
 Se você precisa marcar uma classe como tendo uma característica específica (marcador), em geral, use um atributo personalizado em vez de uma interface.  
  
 **FAZER ✓** fornecer pelo menos um tipo que é uma implementação de uma interface.  
  
 Fazer isso ajuda a validar o design da interface. Por exemplo, <xref:System.Collections.Generic.List%601> é uma implementação do <xref:System.Collections.Generic.IList%601> interface.  
  
 **FAZER ✓** fornecer pelo menos uma API que consome cada interface que você definir (um método de interface como um parâmetro ou uma propriedade digitada como a interface).  
  
 Fazer isso ajuda a validar o design de interface. Por exemplo, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consome o <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.  
  
 **X não** adicionar membros a uma interface que tiver enviado anteriormente.  
  
 Isso interrompe implementações da interface. Você deve criar uma nova interface para evitar problemas de controle de versão.  
  
 Exceto situações descritas nessas diretrizes, você deve, em geral, escolher classes em vez de interfaces na criação de bibliotecas reutilizáveis de código gerenciado.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
