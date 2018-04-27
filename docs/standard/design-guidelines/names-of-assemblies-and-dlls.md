---
title: Nomes de DLLs e Assemblies
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ff14d3d804329e591486a7eb2a2ee7ed430f622c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="names-of-assemblies-and-dlls"></a>Nomes de DLLs e Assemblies
Um assembly é a unidade de implantação e a identidade de programas de código gerenciado. Embora os assemblies podem abranger um ou mais arquivos, normalmente um assembly mapeia um para um com uma DLL. Portanto, esta seção descreve somente DLL convenções de nomenclatura, que podem ser mapeadas para convenções de nomenclatura do assembly.  
  
 **FAZER ✓** Escolha nomes do seu conjunto de DLLs que sugerem grandes blocos de funcionalidade, como System. Data.  
  
 Nomes de assembly e a DLL não precisam corresponder aos nomes de namespace, mas é aconselhável ao nomear assemblies, siga o nome do namespace. Uma boa regra prática é nomear a DLL com base no prefixo comum dos namespaces contidos no assembly. Por exemplo, um assembly com dois namespaces, `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature`, poderia ser chamado `MyCompany.MyTechnology.dll`.  
  
 **✓ CONSIDERE** nomenclatura DLLs de acordo com o seguinte padrão:  
  
 `<Company>.<Component>.dll`  
  
 onde `<Component>` contém uma ou mais cláusulas separados por pontos. Por exemplo:  
  
 `Litware.Controls.dll`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
