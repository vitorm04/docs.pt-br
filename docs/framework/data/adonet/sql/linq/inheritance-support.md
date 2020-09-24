---
title: Suporte à herança
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 7673e69458d5c1af854747c43ba463332a9cd588
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158247"
---
# <a name="inheritance-support"></a>Suporte à herança

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte ao *mapeamento de tabela única*. Ou seja uma hierarquia completa de herança é armazenada em uma única tabela de base de dados. A tabela contém aplainada a união de todas as colunas de dados possíveis para a hierarquia inteira. (Uma União é o resultado da combinação de duas tabelas em uma tabela que tem as linhas que estavam presentes em qualquer uma das tabelas originais.) Cada linha tem nulos nas colunas que não se aplicam ao tipo da instância representada pela linha.  
  
 A estratégia de mapeamento de tabela única é a representação mais simples de herança e fornece características de desempenho bom para várias categorias diferentes de consultas.  
  
 Para implementar esse mapeamento em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você deve especificar atributos e propriedades de atributo na classe raiz da hierarquia de herança. Para obter mais informações, consulte [como mapear hierarquias de herança](how-to-map-inheritance-hierarchies.md).  
  
 Os desenvolvedores que usam o Visual Studio também podem usar o Object Relational Designer para mapear hierarquias de herança.  
  
## <a name="see-also"></a>Confira também

- [Informações gerais](background-information.md)
