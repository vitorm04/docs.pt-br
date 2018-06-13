---
title: Suporte à herança
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 3d396632902b178eee34801a9716d8aa222a08d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359556"
---
# <a name="inheritance-support"></a>Suporte à herança
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte a *mapeamento de tabela única*. Ou seja uma hierarquia completa de herança é armazenada em uma única tabela de base de dados. A tabela contém aplainada a união de todas as colunas de dados possíveis para a hierarquia inteira. (A união de é o resultado de combinar duas tabelas em uma tabela que possui as linhas que estaram presente em qualquer uma das tabelas originais.) Cada linha tem nulos em colunas que não se aplicam ao tipo da instância representada por linha.  
  
 A estratégia de mapeamento de tabela única é a representação mais simples de herança e fornece características de desempenho bom para várias categorias diferentes de consultas.  
  
 Para implementar esse mapeamento em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você deve especificar atributos e propriedades de atributo na classe raiz da hierarquia de herança. Para obter mais informações, consulte [como: hierarquias de herança de mapa](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Os desenvolvedores usando o Visual Studio também podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear hierarquias de herança.  
  
## <a name="see-also"></a>Consulte também  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
