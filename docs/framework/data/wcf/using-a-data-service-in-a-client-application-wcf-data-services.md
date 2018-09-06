---
title: Usando um serviço de dados em um aplicativo cliente (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 092f073a138a09fc25b96fbddde5b73992056981
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732242"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Usando um serviço de dados em um aplicativo cliente (WCF Data Services)
Você pode acessar um serviço que expõe um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed, fornecendo um URI para um navegador da Web. O URI fornece o endereço de um recurso e, em seguida, são enviadas a esses endereços mensagens de solicitação para acessar ou alterar os dados subjacentes que o recurso representa. O navegador emite um comando HTTP GET e retorna o recurso solicitado como um feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Para obter mais informações, consulte [acessar o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Embora um navegador da Web possa ser útil para testar se um recurso [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] retorna os dados esperados, os serviços [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de produção que permitem criar, atualizar e excluir os dados são geralmente acessados pelo código do aplicativo ou por linguagens de script em uma página da Web. Este tópico fornece uma visão geral de como acessar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds de um aplicativo cliente.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Acessando e alterando dados usando a semântica REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ajuda a garantir a interoperabilidade entre os serviços que expõem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds e aplicativos que consomem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds. Os aplicativos acessam e alterar dados em um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-com base em serviço enviando mensagens de solicitação de uma ação de HTTP específica e com um URI que direciona um recurso de entidade com relação à qual a ação deve ser executada. Quando os dados de entidade devem ser fornecidos, eles são fornecidos como uma carga especificamente codificada no corpo da mensagem.  
  
### <a name="http-actions"></a>Ações HTTP  
 O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] oferece suporte às seguintes ações HTTP para executar operações de criação, leitura, atualização e exclusão nos dados de entidade que o recurso direcionado representa:  
  
-   **HTTP GET** -isso é a ação padrão quando um recurso é acessado a partir de um navegador. Nenhuma carga é fornecida na mensagem de solicitação, e é retornado um método de resposta com uma carga que contém os dados solicitados.  
  
-   **HTTP POST** -insere novos dados de entidade no recurso fornecido. Os dados a serem inseridos são fornecidos na carga da mensagem de solicitação. A carga da mensagem de resposta contém os dados da entidade recém-criada. Isso inclui os valores de chave gerados automaticamente. O cabeçalho também contém o URI que direciona o novo recurso de entidade.  
  
-   **HTTP DELETE** -exclui os dados de entidade que representa o recurso especificado. Não há uma carga presente nas mensagens de resposta ou solicitação.  
  
-   **HTTP PUT** - substitui dados de entidade no recurso solicitado com novos dados que são fornecidos na carga da mensagem de solicitação existentes.  
  
-   **HTTP MERGE** – devido a ineficiências na execução de uma exclusão seguida por uma inserção na fonte de dados apenas para alterar dados de entidade, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] introduz uma nova ação HTTP MERGE. A carga da mensagem de solicitação contém as propriedades que devem ser alteradas no recurso de entidade direcionado. Como o HTTP MERGE não é definido na especificação HTTP, ele pode exigir processamento adicional para encaminhar uma solicitação HTTP MERGE através de servidores que não reconhecem o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 Para obter mais informações, consulte [OData: operações](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formatos de carga  
 Para uma solicitação HTTP PUT, HTTP POST ou HTTP MERGE, a carga de uma mensagem de solicitação contém os dados de entidade que você envia ao serviço de dados. O conteúdo da carga depende do formato de dados da mensagem. As respostas HTTP a todas as ações, exceto DELETE, também contêm tal carga. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dá suporte aos seguintes formatos de carga para acessar e alterar dados com o serviço:  
  
-   **Atom** -com base em XML de uma mensagem de codificação que é definido pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] como uma extensão do protocolo de publicação Atom (AtomPub) para habilitar a troca de dados via HTTP para feeds da Web, podcasts, wikis e funcionalidade de Internet baseado em XML. Para obter mais informações, consulte [OData: formato Atom](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** -notação JSON (JavaScript Object) é um formato de intercâmbio de dados leve que é baseado em um subconjunto da linguagem de programação JavaScript. Para obter mais informações, consulte [OData: formato JSON](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 O formato de mensagem da carga é solicitado no cabeçalho da mensagem de solicitação HTTP. Para obter mais informações, consulte [OData: operações](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Acessando e alterando dados usando bibliotecas de cliente  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui bibliotecas de cliente que permitem que você consumam mais facilmente um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed do .NET Framework e aplicativos cliente baseados no Silverlight. Essas bibliotecas simplificam o envio e o recebimento de mensagens HTTP. Elas também convertem a carga da mensagem em objetos CLR que representam dados de entidade. As bibliotecas de cliente apresentam as duas classes principais <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601>. Essas classes permitem consultar um serviço de dados e, em seguida, trabalhar com os dados de entidade retornados como objetos CLR. Para obter mais informações, consulte [biblioteca de cliente do WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) e [WCF Data Services (Silverlight)](https://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Você pode usar o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência a um serviço de dados. Essa ferramenta solicita os metadados de serviço de um serviço de dados referenciado e gera o <xref:System.Data.Services.Client.DataServiceContext> que representa um serviço de dados, além de gerar as classes de serviço de dados cliente que representam entidades. Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Há bibliotecas de programação disponíveis que você pode usar para consumir um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em outros tipos de aplicativos cliente. Para obter mais informações, consulte o [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Consulte também  
 [Acessando recursos do serviço de dados](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)
