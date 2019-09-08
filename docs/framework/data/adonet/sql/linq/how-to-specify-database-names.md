---
title: 'Como: especificar nomes de banco de dados'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781580"
---
# <a name="how-to-specify-database-names"></a>Como: especificar nomes de banco de dados
Use a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> em um atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para especificar o nome de uma base de dados quando um nome não é fornecido pela conexão.  
  
 Para exemplos de códigos, consulte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Para especificar o nome de base de dados  
  
1. Adicione o atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para a declaração de classe para o base de dados.  
  
2. Adicione a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ao atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> .  
  
3. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> o nome que você deseja especificar.  
  
## <a name="see-also"></a>Consulte também

- [O modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Como: Personalizar classes de entidade usando o editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md)
