---
title: 'Como: Personalizar Feeds com o provedor do Entity Framework (WCF Data Services)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55bab1ad9ff9ebad348624a3b35c2a5b49541f48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Como: Personalizar Feeds com o provedor do Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite que você personalize a serialização Atom em uma resposta do serviço de dados para que as propriedades de uma entidade podem ser mapeadas para elementos não utilizados são definidos no protocolo de AtomPub. Este tópico mostra como definir atributos de mapeamento para tipos de entidade em um modelo de dados que é definido em um arquivo. edmx usando o provedor do Entity Framework. Para obter mais informações, consulte [personalização Feed](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Neste tópico, você será modificar manualmente o arquivo. edmx gerados por ferramenta que contém o modelo de dados. Você deve modificar manualmente o arquivo porque não há suporte para extensões para o modelo de dados Entity Designer. Para obter mais informações sobre o arquivo. edmx que geram as ferramentas do modelo de dados de entidade, consulte [. edmx visão geral do arquivo](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4). O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Para modificar manualmente o arquivo Northwind.edmx para adicionar atributos de personalização de feed  
  
1.  Em **Solution Explorer**, com o botão direito do `Northwind.edmx` de arquivo e, em seguida, clique em **abrir com**.  
  
2.  No **abrir com - Northwind.edmx** caixa de diálogo, selecione **Editor XML**e, em seguida, clique em **Okey**.  
  
3.  Localize o `ConceptualModels` elemento e substituir a existente `Customers` tipo de entidade com o seguinte elemento que contém atributos de mapeamento de personalização de feed:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Salvar as alterações e feche o arquivo Northwind.edmx.  
  
5.  (Opcional) Clique no arquivo Northwind.edmx e, em seguida, clique em **executar personalizado ferramenta**.  
  
     Isso gera novamente o arquivo de camada de objeto, que pode ser necessário.  
  
6.  Recompile o projeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo anterior retorna o resultado a seguir para o URI `http://myservice/``Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Consulte também  
 [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)
