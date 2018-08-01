---
title: Sobrecarga de membro
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c77f08cd573dc40083718b783ae01233ca00766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573549"
---
# <a name="member-overloading"></a>Sobrecarga de membro
Membro sobrecarga significa criar dois ou mais membros do mesmo tipo que diferem apenas o número ou tipo de parâmetros, mas que têm o mesmo nome. Por exemplo, em seguida, o `WriteLine` método está sobrecarregado:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Como somente métodos, construtores e propriedades indexadas podem ter parâmetros, somente os membros podem ser sobrecarregados.  
  
 Sobrecarga é uma das técnicas mais importantes para melhorar a legibilidade de bibliotecas reutilizáveis, produtividade e usabilidade. Sobrecarga no número de parâmetros torna possível fornecer versões mais simples de construtores e métodos. Sobrecarga no tipo de parâmetro torna possível usar o mesmo nome de membro para executar operações idênticas em um conjunto selecionado de tipos diferentes de membros.  
  
 **✓ DO** tente usar nomes de parâmetro descritivo para indicar o padrão usado por sobrecargas mais curto.  
  
 **X AVOID** arbitrariamente diversos nomes de parâmetro em sobrecargas. Se um parâmetro em uma sobrecarga representa a mesma entrada como um parâmetro em outra sobrecarga, os parâmetros devem ter o mesmo nome.  
  
 **X AVOID** inconsistentes na ordem de parâmetros na sobrecarga membros. Parâmetros com o mesmo nome devem aparecer na mesma posição em todas as sobrecargas.  
  
 **✓ DO** fazer somente a maior sobrecarga virtual (se extensibilidade é necessária). Sobrecargas menores devem simplesmente chamar por meio de uma sobrecarga maior.  
  
 **X DO NOT** usar `ref` ou `out` modificadores para sobrecarregar membros.  
  
 Alguns idiomas não é possível resolver chamadas para sobrecargas assim. Além disso, essas sobrecargas geralmente tem semântica completamente diferente e provavelmente não devem ser sobrecargas mas dois métodos separados em vez disso.  
  
 **X DO NOT** têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, mas com semânticas diferentes.  
  
 **✓ DO** permitir `null` a serem passados para os argumentos opcionais.  
  
 **✓ DO** usar membro sobrecarga em vez de definir membros com argumentos padrão.  
  
 Argumentos padrão não são compatível com CLS.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
