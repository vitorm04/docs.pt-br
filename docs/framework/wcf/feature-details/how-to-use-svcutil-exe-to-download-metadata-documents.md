---
title: Como usar o Svcutil.exe para baixar documentos de metadados
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: c04b63fa4963a5df0f910da8702643a6484a4edd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596923"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Como usar o Svcutil.exe para baixar documentos de metadados
Você pode usar svcutil. exe para baixar metadados de serviços em execução e para salvar os metadados em arquivos locais. Para esquemas de URL HTTP e HTTPS, svcutil. exe tenta recuperar metadados usando o WS-MetadataExchange e a [descoberta de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)). Para todos os outros esquemas de URL, svcutil. exe usa apenas WS-MetadataExchange.  
  
 Por padrão, svcutil. exe usa as associações definidas na <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe. Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para SvcUtil. exe (svcutil. exe. config) que usa o `IMetadataExchange` contrato e que tem o mesmo nome que o esquema de Uniform Resource Identifier (URI) do endereço do ponto de extremidade de metadados.  
  
> [!CAUTION]
> Ao executar svcutil. exe para obter metadados para um serviço que expõe dois contratos de serviço diferentes que cada um contém uma operação de mesmo nome, svcutil. exe exibe um erro dizendo "não é possível obter metadados de...". Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado `ICarService` que tem uma operação `Get(Car c)` e o mesmo serviço expõe um contrato de serviço chamado `IBookService` que tem uma operação `Get(Book b)` . Para contornar esse problema, adote uma das seguintes medidas:
>
> - Renomeie uma das operações.
> - Defina <xref:System.ServiceModel.OperationContractAttribute.Name%2A> como um nome diferente.
> - Defina um dos namespaces de operações para um namespace diferente usando a <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Para baixar metadados usando svcutil. exe  
  
1. Localize a ferramenta svcutil. exe no seguinte local:  
  
     C:\Arquivos de Programas\microsoft SDKs\Windows\v1.0.\bin  
  
2. No prompt de comando, inicie a ferramenta usando o formato a seguir.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Você deve especificar a `/t:metadata` opção para baixar metadados. Caso contrário, o código do cliente e a configuração serão gerados.  
  
3. O `url` argumento <>especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedado online. O `epr` argumento <> especifica o caminho para um arquivo XML que contém um WS-Addressing `EndpointAddress` para um ponto de extremidade de serviço que oferece suporte a WS-MetadataExchange.  
  
 Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Exemplo  
 O comando a seguir baixa os documentos de metadados de um serviço em execução.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Consulte também

- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
