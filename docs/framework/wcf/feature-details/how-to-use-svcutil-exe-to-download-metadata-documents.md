---
title: Como usar o Svcutil.exe para baixar documentos de metadados
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 6643f0a5dba98afcef38870cf24d91e7d69a1440
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481852"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Como usar o Svcutil.exe para baixar documentos de metadados
Você pode usar Svcutil.exe para baixar os metadados de serviços em execução e salvar os metadados em arquivos locais. Para esquemas de URL HTTP e HTTPS, Svcutil.exe tenta recuperar metadados usando WS-MetadataExchange e [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950). Para todos os outros esquemas de URL, Svcutil.exe usa apenas WS-MetadataExchange.  
  
 Por padrão, Svcutil.exe usa as associações definidas a <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe. Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para Svcutil.exe (svcutil) que usa o `IMetadataExchange` contrato e que tem o mesmo nome como o identificador de URI (Uniform Resource) esquema do endereço do ponto de extremidade de metadados.  
  
> [!CAUTION]
> Quando em execução Svcutil.exe ao obter metadados para um serviço que expõe dois serviços diferentes de contratos que contêm uma operação de mesmo nome, Svcutil.exe exibe um erro dizendo que "Não é possível obter metadados de..." Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado `ICarService` que tem uma operação `Get(Car c)` e o mesmo serviço expõe um contrato de serviço chamado `IBookService` que tem uma operação `Get(Book b)`. Para contornar esse problema, siga um destes procedimentos:
>
> - Renomeie uma das operações.
> - Defina o <xref:System.ServiceModel.OperationContractAttribute.Name%2A> para um nome diferente.
> - Defina um dos namespaces das operações em um namespace diferente usando o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Para baixar os metadados usando Svcutil.exe  
  
1.  Localize a ferramenta Svcutil.exe no seguinte local:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  No prompt de comando, inicie a ferramenta usando o seguinte formato.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Você deve especificar o `/t:metadata` opção para baixar os metadados. Caso contrário, a configuração e o código de cliente são gerados.  
  
3.  O <`url`> argumento especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedado online. O <`epr`> argumento especifica o caminho para um arquivo XML que contém um WS-Addressing `EndpointAddress` para um ponto de extremidade de serviço que dá suporte a WS-MetadataExchange.  
  
 Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Exemplo  
 O comando a seguir baixa documentos de metadados de um serviço em execução.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
