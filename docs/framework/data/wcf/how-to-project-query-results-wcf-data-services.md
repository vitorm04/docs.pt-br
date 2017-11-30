---
title: 'Como: projeto resultados da consulta (WCF Data Services)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b3e6b05952dfc87a911b1a80582cd27b327d6a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Como: projeto resultados da consulta (WCF Data Services)
Projeção fornece um mecanismo para reduzir a quantidade de dados retornados por uma consulta especificando que somente algumas propriedades de uma entidade são retornadas na resposta. Você pode executar as projeções nos resultados de uma [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] de consulta usando o `$select` opção de consulta ou usando o [selecione](~/docs/csharp/language-reference/keywords/select-clause.md) cláusula ([selecione](~/docs/visual-basic/language-reference/queries/select-clause.md) no Visual Basic) em uma consulta LINQ. Para obter mais informações, consulte [consultando o Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma consulta LINQ que projetos entidades de clientes em um novo tipo CustomerAddress, que contém apenas as propriedades de endereço específico e a propriedade de identidade. Isso `CustomerAddress` classe é definida no cliente e é atribuído para que a biblioteca de cliente possa reconhecer como um tipo de entidade.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um LINQ a consulta que entidades de clientes retornado de projetos em um novo tipo de CustomerAddressNonEntity, que contém propriedades específicas de endereço apenas e nenhuma propriedade de identidade. Isso `CustomerAddressNonEntity` classe é definida no cliente e não é atribuído como um tipo de entidade.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra as definições do `CustomerAddress``CustomerAddressNonEntity` tipos que são usados nos exemplos anteriores.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
