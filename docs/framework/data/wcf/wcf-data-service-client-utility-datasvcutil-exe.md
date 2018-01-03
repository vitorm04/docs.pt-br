---
title: "Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcbbbe5180acaf943956310d4837a105d8d049d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)
DataSvcUtil.exe é uma ferramenta de linha de comando fornecida pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] que consome um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed e gera as classes de serviço de dados do cliente que são necessárias para acessar um serviço de dados de um aplicativo cliente .NET Framework. Esse utilitário pode gerar classes de dados usando as seguintes fontes de metadados:  
  
-   O URI de um serviço de dados raiz. O utilitário solicita o documento de metadados de serviço, que descreve o modelo de dados exposto pelo serviço de dados. Para obter mais informações, consulte [OData: documento de metadados de serviço](http://go.microsoft.com/fwlink/?LinkId=186070).  
  
-   Um arquivo de modelo de dados (. CSDL) definido usando a linguagem de definição de esquema conceitual (CSDL), conforme definido no [ \[MC CSDL\]: formato de arquivo de definição de esquema conceitual](http://go.microsoft.com/fwlink/?LinkID=159072) especificação.  
  
-   Um arquivo. edmx criado usando as ferramentas de modelo de dados de entidade são fornecidas com o Entity Framework. Para obter mais informações, consulte o [ \[MC EDMX\]: modelo de dados de entidade para formato de empacotamento de serviços de dados](http://go.microsoft.com/fwlink/?LinkID=178833) especificação.  
  
 Para obter mais informações, consulte [como: manualmente gerar cliente dados Classes de serviço](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
 A ferramenta DataSvcUtil.exe está instalada no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory. Em muitos casos, ele está localizado em C:\Windows\Microsoft.NET\Framework\v4.0. Para sistemas de 64 bits, ele está localizado em C:\Windows\Microsoft.NET\Framework64\v4.0. Você também pode acessar a ferramenta DataSvcUtil.exe do prompt de comando do Visual Studio (clique **iniciar**, aponte para **todos os programas**, aponte para **Microsoft Visual Studio 2010**, aponte para **ferramentas do Visual Studio**e, em seguida, clique em **Prompt de comando do Visual Studio 2010**).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/dataservicecollection`|Especifica que o código necessário para associar objetos a controles também é gerado.|  
|`/help`<br /><br /> -ou-<br /><br /> `/?`|Exibe sintaxe de comando e opções para a ferramenta.|  
|`/in:` *\<arquivo >*|Especifica o arquivo. CSDL ou. edmx ou um diretório onde o arquivo está localizado.|  
|`/language:`[VB &#124; CSharp]|Especifica a linguagem dos arquivos de código-fonte gerados. A linguagem volta automaticamente para C#.|  
|`/nologo`|Suprime a notificação de direitos autorais da exibição.|  
|`/out:` *\<arquivo >*|Especifica o nome do arquivo de código fonte que contém as classes de serviço de dados de cliente gerada.|  
|`/uri:` *\<cadeia de caracteres >*|O URI do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.|  
|`/version:`[1.0&#124;2.0]|Especifica a versão mais recente aceita de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. A versão é determinada com base no `DataServiceVersion` atributo do elemento ' DataService ' nos metadados do serviço de dados retornados. Para obter mais informações, consulte [controle de versão de serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md). Quando você especifica o `/dataservicecollection` parâmetro, você deve especificar também `/version:2.0` para habilitar a associação de dados.|  
  
## <a name="see-also"></a>Consulte também  
 [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)  
 [Como adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
