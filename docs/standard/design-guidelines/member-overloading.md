---
title: Sobrecarga de membro
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b54a99ab88e4cfa0569b2095a0be3750c91f244
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
  
 **FAZER ✓** tente usar nomes de parâmetro descritivo para indicar o padrão usado por sobrecargas mais curto.  
  
 **X Evite** arbitrariamente diversos nomes de parâmetro em sobrecargas. Se um parâmetro em uma sobrecarga representa a mesma entrada como um parâmetro em outra sobrecarga, os parâmetros devem ter o mesmo nome.  
  
 **X Evite** inconsistentes na ordem de parâmetros na sobrecarga membros. Parâmetros com o mesmo nome devem aparecer na mesma posição em todas as sobrecargas.  
  
 **FAZER ✓** fazer somente a maior sobrecarga virtual (se extensibilidade é necessária). Sobrecargas menores devem simplesmente chamar por meio de uma sobrecarga maior.  
  
 **X não** usar `ref` ou `out` modificadores para sobrecarregar membros.  
  
 Alguns idiomas não é possível resolver chamadas para sobrecargas assim. Além disso, essas sobrecargas geralmente tem semântica completamente diferente e provavelmente não devem ser sobrecargas mas dois métodos separados em vez disso.  
  
 **X não** têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, mas com semânticas diferentes.  
  
 **FAZER ✓** permitir `null` a serem passados para os argumentos opcionais.  
  
 **FAZER ✓** usar membro sobrecarga em vez de definir membros com argumentos padrão.  
  
 Argumentos padrão não são compatível com CLS.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
