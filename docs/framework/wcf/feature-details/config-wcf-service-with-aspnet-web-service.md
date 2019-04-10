---
title: 'Como: configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 84762d8917609b84a049ea665b575acfa6e5fecf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325183"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Como: configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET
Para configurar um ponto de extremidade de serviço do Windows Communication Foundation (WCF) para interoperabilidade com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] clientes de serviço Web, use o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tipo como o tipo de associação para o ponto de extremidade de serviço.  
  
 Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Clientes de serviço Web não dão suporte para a codificação de mensagem MTOM, portanto, o <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade deve ser deixada como seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Clientes de serviço Web do ASP.Net não dão suporte a WS-Security, portanto, o <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> deve ser definido como <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Para disponibilizar para os metadados para um serviço WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web ferramentas de geração de proxy de serviço (ou seja, [ferramenta do Web Services Description Language (Wsdl.exe)](https://go.microsoft.com/fwlink/?LinkId=73833), [ferramenta de descoberta de serviços da Web (Disco.exe)](https://go.microsoft.com/fwlink/?LinkId=73834)e o recurso Add Web Reference do Visual Studio), você deve expor um ponto de extremidade de metadados HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Para adicionar um ponto de extremidade do WCF que é compatível com clientes de serviço Web do ASP.NET no código  
  
1. Criar um novo <xref:System.ServiceModel.BasicHttpBinding> instância  
  
2. Opcionalmente, habilitar a segurança de transporte para essa associação de ponto de extremidade de serviço, definindo o modo de segurança para a associação se <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Para obter detalhes, consulte [segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Adicione um novo ponto de extremidade do aplicativo para seu host de serviço usando a instância de associação que você acabou de criar. Para obter detalhes sobre como adicionar um ponto de extremidade de serviço no código, consulte o [como: Criar um ponto de extremidade de serviço no código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Habilite um ponto de extremidade de metadados HTTP/GET para o seu serviço. Para obter detalhes, consulte [como: Publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Para adicionar um ponto de extremidade do WCF que é compatível com clientes de serviço Web do ASP.NET em um arquivo de configuração  
  
1. Criar um novo <xref:System.ServiceModel.BasicHttpBinding> configuração de associação. Para obter detalhes, consulte o [como: Especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Opcionalmente, habilitar a segurança de transporte para essa configuração de associação de ponto de extremidade de serviço, definindo o modo de segurança para a associação se <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Para obter detalhes, consulte [segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Configure um novo ponto de extremidade do aplicativo para seu serviço usando a configuração de associação que você acabou de criar. Para obter detalhes sobre como adicionar um ponto de extremidade de serviço em um arquivo de configuração, consulte o [como: Criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Habilite um ponto de extremidade de metadados HTTP/GET para o seu serviço. Para obter detalhes, consulte o [como: Publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar um ponto de extremidade do WCF que é compatível com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] clientes de serviço no código da Web e, opcionalmente, nos arquivos de configuração.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Consulte também

- [Como: criar um ponto de extremidade de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Como: publicar metadados utilizando código para um serviço](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Como: criar um ponto de extremidade de serviço em configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Como: publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Utilizando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
