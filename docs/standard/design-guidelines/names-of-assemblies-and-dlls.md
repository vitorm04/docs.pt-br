---
title: Nomes dos Assemblies e DLLs
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97bd152cff53fb1c2edb107b6d6b34bd91ca1c49
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276309"
---
# <a name="names-of-assemblies-and-dlls"></a>Nomes dos Assemblies e DLLs
Um assembly é a unidade de implantação e identidade para programas de código gerenciado. Embora os assemblies podem abranger um ou mais arquivos, normalmente um assembly mapeia um para um com uma DLL. Portanto, esta seção descreve somente DLL convenções de nomenclatura, que, em seguida, podem ser mapeadas para as convenções de nomenclatura do assembly.  
  
 **✓ DO** Escolha nomes do seu conjunto de DLLs que sugerem grandes blocos de funcionalidade, como System. Data.  
  
 Nomes de assembly e a DLL não precisam corresponder aos nomes de namespace, mas é razoável seguir o nome do namespace ao nomear os assemblies. Uma boa regra prática é nomear a DLL com base no prefixo comum dos namespaces contidos no assembly. Por exemplo, um assembly com dois namespaces, `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature`, poderia ser chamado `MyCompany.MyTechnology.dll`.  
  
 **✓ CONSIDER** nomenclatura DLLs de acordo com o seguinte padrão:  
  
 `<Company>.<Component>.dll`  
  
 onde `<Component>` contém uma ou mais cláusulas separados por pontos. Por exemplo:  
  
 `Litware.Controls.dll`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
