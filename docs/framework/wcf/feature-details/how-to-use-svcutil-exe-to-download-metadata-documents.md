---
title: Como usar o Svcutil.exe para baixar documentos de metadados
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: a8872bbf04e688906fb0229e3d8215fb92cdbc3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492392"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Como usar o Svcutil.exe para baixar documentos de metadados
Você pode usar o Svcutil.exe para baixar os metadados da execução de serviços e para salvar os metadados em arquivos locais. Para esquemas de URL HTTP e HTTPS, o Svcutil.exe tenta recuperar metadados de WS-MetadataExchange e [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950). Para todos os outros esquemas de URL, Svcutil.exe usa apenas o WS-MetadataExchange.  
  
 Por padrão, o Svcutil.exe usa as associações definidas no <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe. Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para Svcutil.exe (svcutil.exe.config) que usa o `IMetadataExchange` contrato e que tem o mesmo nome como o identificador de URI (Uniform Resource) esquema de endereço de ponto de extremidade de metadados.  
  
> [!CAUTION]
>  Ao executar o Svcutil.exe para obter metadados para um serviço que expõe dois serviços diferentes contratos que contêm uma operação de mesmo nome, Svcutil.exe exibe um erro dizendo "Não é possível obter metadados de..." Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado ICarService que tem uma operação obter (Car c) e o mesmo serviço expõe um contrato de serviço chamado IBookService que tem uma operação Get (catálogo b). Para contornar esse problema, siga um destes procedimentos:  
>   
>  -   Renomear uma das operações  
> -   Definir o <xref:System.ServiceModel.OperationContractAttribute.Name%2A> para um nome diferente.  
> -   Defina um dos namespaces as operações em um namespace diferente usando o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Para baixar os metadados usando Svcutil.exe  
  
1.  Localize a ferramenta Svcutil.exe no seguinte local:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  No prompt de comando, inicie a ferramenta usando o formato a seguir.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Você deve especificar o `/t:metadata` opção para fazer o download de metadados. Caso contrário, a configuração e o código do cliente são gerados.  
  
3.  O <`url`> argumento especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedada online. O <`epr`> argumento especifica o caminho para um arquivo XML que contém o WS-Addressing `EndpointAddress` para um ponto de extremidade de serviço que dá suporte ao WS-MetadataExchange.  
  
 Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Exemplo  
 O comando a seguir faz o download de documentos de metadados de um serviço em execução.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
