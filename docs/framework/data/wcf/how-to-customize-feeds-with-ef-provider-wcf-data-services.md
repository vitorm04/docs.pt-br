---
title: 'Como: Personalizar Feeds com o provedor do Entity Framework (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 186b921f508b1a4b05e766c4f1a3c9e65de04722
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089283"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Como: Personalizar Feeds com o provedor do Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite personalizar a serialização Atom em uma resposta do serviço de dados para que as propriedades de uma entidade podem ser mapeadas para elementos não utilizados que são definidos no protocolo AtomPub. Este tópico mostra como definir atributos de mapeamento para tipos de entidade em um modelo de dados que é definido em um arquivo. edmx, usando o provedor do Entity Framework. Para obter mais informações, consulte [personalização de Feed](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Neste tópico, você será modificar manualmente o gerados por ferramenta arquivo. edmx que contém o modelo de dados. Você deve modificar manualmente o arquivo porque não há suporte para extensões para o modelo de dados pelo Designer de entidade. Para obter mais informações sobre o arquivo. edmx que geram as ferramentas do modelo de dados de entidade, consulte [. edmx visão geral do arquivo (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Para modificar manualmente o arquivo EDMX para adicionar atributos de personalização de feed  
  
1.  No **Gerenciador de soluções**, com o botão direito do `Northwind.edmx` de arquivo e, em seguida, clique em **abrir com**.  
  
2.  No **abrir com - EDMX** caixa de diálogo, selecione **Editor de XML**e, em seguida, clique em **Okey**.  
  
3.  Localize o `ConceptualModels` elemento e substituir o existente `Customers` tipo de entidade com o seguinte elemento que contém atributos de mapeamento de personalização do feed:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Salve as alterações e feche o arquivo EDMX.  
  
5.  (Opcional) O arquivo EDMX com o botão direito e, em seguida, clique em **executar ferramenta personalizada**.  
  
     Isso gera novamente o arquivo de camada de objeto, que pode ser necessário.  
  
6.  Recompile o projeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo anterior retorna o resultado a seguir para o URI `http://myservice/Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Consulte também

- [Provedor de Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
