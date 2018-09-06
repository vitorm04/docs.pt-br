---
title: Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 7c9b713571cea3d2c8c5f6511f2cfab7e87b80ee
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739185"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)

DataSvcUtil.exe é uma ferramenta de linha de comando fornecida pelo WCF Data Services que consome um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed e gera as classes de serviço de dados do cliente que são necessários para acessar um serviço de dados de um aplicativo de cliente do .NET Framework. Esse utilitário pode gerar classes de dados usando as seguintes fontes de metadados:

-   O URI de um serviço de dados raiz. O utilitário solicita o documento de metadados de serviço, que descreve o modelo de dados exposto pelo serviço de dados. Para obter mais informações, consulte [OData: documento de metadados de serviço](https://go.microsoft.com/fwlink/?LinkId=186070).

-   Um arquivo de modelo de dados (. CSDL) definido usando a linguagem de definição de esquema conceitual (CSDL), conforme definido na [ \[CSDL MC\]: formato de arquivo de definição de esquema conceitual](https://go.microsoft.com/fwlink/?LinkID=159072) especificação.

-   Um arquivo. edmx criado usando as ferramentas do modelo de dados de entidade que são fornecidas com o Entity Framework. Para obter mais informações, consulte o [ \[MC-EDMX\]: modelo de dados de entidade para formato de empacotamento de serviços de dados](https://go.microsoft.com/fwlink/?LinkID=178833) especificação.

Para obter mais informações, consulte [como: manualmente gerar dados de Classes de serviço cliente](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

A ferramenta DataSvcUtil.exe é instalada no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory. Em muitos casos, ele fica localizado no *C:\Windows\Microsoft.NET\Framework\v4.0*. Para sistemas de 64 bits, ele fica localizado no *C:\Windows\Microsoft.NET\Framework64\v4.0*. Você também pode acessar a ferramenta DataSvcUtil.exe no Prompt de comando do desenvolvedor para Visual Studio.

## <a name="syntax"></a>Sintaxe

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

### <a name="parameters"></a>Parâmetros

|Opção|Descrição|
|------------|-----------------|
|`/dataservicecollection`|Especifica que o código necessário para associar objetos a controles também é gerado.|
|`/help`<br /><br /> -ou-<br /><br /> `/?`|Exibe sintaxe de comando e opções para a ferramenta.|
|`/in:` *\<arquivo >*|Especifica o arquivo. CSDL ou. edmx ou um diretório em que o arquivo está localizado.|
|`/language:`[VB&#124;CSharp]|Especifica a linguagem dos arquivos de código-fonte gerados. A linguagem volta automaticamente para C#.|
|`/nologo`|Suprime a notificação de direitos autorais da exibição.|
|`/out:` *\<arquivo >*|Especifica o nome do arquivo de código fonte que contém as classes de serviço de dados do cliente gerado.|
|`/uri:` *\<cadeia de caracteres >*|O URI do feed OData.|
|`/version:`[1.0&#124;2.0]|Especifica a versão mais recente aceita do OData. A versão é determinada com base no `DataServiceVersion` atributo do elemento DataService nos metadados do serviço de dados retornados. Para obter mais informações, consulte [controle de versão de serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md). Quando você especifica o `/dataservicecollection` parâmetro, você também deve especificar `/version:2.0` para habilitar a associação de dados.|

## <a name="see-also"></a>Consulte também

- [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)
- [Como adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
