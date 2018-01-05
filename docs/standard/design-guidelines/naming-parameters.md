---
title: "Parâmetros de nomeação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a10fa8835bfbcf826f8a3bb9318966e0dc603864
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-parameters"></a>Parâmetros de nomeação
Além do motivo óbvio de legibilidade, é importante seguir as diretrizes para nomes de parâmetro porque os parâmetros são exibidos na documentação e no designer quando as ferramentas de design visual fornecem Intellisense e a funcionalidade de navegação de classe.  
  
 **FAZER ✓** use camelCasing em nomes de parâmetro.  
  
 **FAZER ✓** usam nomes de parâmetro descritivo.  
  
 **✓ CONSIDERE** usando nomes com base no significado do parâmetro em vez do tipo do parâmetro.  
  
### <a name="naming-operator-overload-parameters"></a>Parâmetros de sobrecarga de operador de nomenclatura  
 **FAZER ✓** usar `left` e `right` para nomes de parâmetro de sobrecarga de operador binário se não houver nenhum significado para os parâmetros.  
  
 **FAZER ✓** usar `value` para unário operador sobrecarregar os nomes de parâmetro se não houver nenhum significado para os parâmetros.  
  
 **✓ CONSIDERE** nomes significativos para o operador de sobrecarga parâmetros se isso adiciona valor significativo.  
  
 **X não** use abreviações ou índices numéricos para o operador sobrecarregar os nomes de parâmetro.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
