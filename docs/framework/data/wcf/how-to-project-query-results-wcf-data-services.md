---
title: 'Como: resultados da consulta (WCF Data Services) do projeto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: c1eb2618e14f0e02aa5e1a2e91aa93fe0831c7c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508738"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Como: resultados da consulta (WCF Data Services) do projeto
Projeção fornece um mecanismo para reduzir a quantidade de dados retornados por uma consulta, especificando que somente algumas propriedades de uma entidade são retornadas na resposta. Você pode executar as projeções nos resultados de uma [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] consultar usando o `$select` opção de consulta ou usando o [selecionar](~/docs/csharp/language-reference/keywords/select-clause.md) cláusula ([selecione](~/docs/visual-basic/language-reference/queries/select-clause.md) no Visual Basic) em uma consulta LINQ. Para obter mais informações, consulte [consultando o Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma consulta LINQ que projeta entidades Customers em um novo tipo CustomerAddress, que contém a propriedade de identidade além de apenas as propriedades de endereço específico. Isso `CustomerAddress` classe é definida no cliente e é atribuída para que a biblioteca de cliente pode reconhecê-lo como um tipo de entidade.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um LINQ consulta que entidades de clientes projetos retornadas em um novo tipo CustomerAddressNonEntity, que contém as propriedades específicas de endereço somente e nenhuma propriedade de identidade. Isso `CustomerAddressNonEntity` classe é definida no cliente e não está atribuído como um tipo de entidade.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra as definições dos `CustomerAddress` e `CustomerAddressNonEntity` tipos que são usados nos exemplos anteriores.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
