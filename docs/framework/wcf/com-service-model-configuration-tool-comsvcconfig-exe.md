---
title: Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 98c8e50ea4a9efe1c69a0c7b959b228a045dfca1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855661"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
A ferramenta de linha de comando de configuração do modelo de serviço COM+ (ComSvcConfig. exe) permite que você configure as interfaces COM+ para serem expostas como serviços Web.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Você deve ser um administrador no computador local para usar o ComSvcConfig. exe.  
  
 A ferramenta pode ser encontrada no seguinte local  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Para obter mais informações sobre o ComSvcConfig. exe [, consulte Como: Use a ferramenta](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)de configuração do modelo de serviço com+.  
  
 A tabela a seguir descreve os modos que podem ser usados com ComSvcConfig. exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`install`|Instala uma configuração para uma interface COM+ para integração do modelo de serviço.<br /><br /> Forma `/i`abreviada.|  
|`uninstall`|Desinstala uma configuração de uma interface COM+ da integração do modelo de serviço.<br /><br /> Forma `/u`abreviada.|  
|`list`|Lista informações sobre aplicativos COM+ e componentes que têm interfaces configuradas para integração do modelo de serviço.<br /><br /> Forma `/l`abreviada.|  
  
 A tabela a seguir descreve os sinalizadores que podem ser usados com ComSvcConfig. exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/application:` \<*ApplicationID* &#124; *ApplicationName*\>|Especifica o aplicativo COM+ a ser configurado.<br /><br /> Forma `/a`abreviada.|  
|`/contract:`&#124; &#124; &#124; Progidid deClassID,interfacedeinterface\* \<&#124;    \*\>|Especifica o componente e a interface COM+ que serão configurados como o contrato para o serviço.<br /><br /> Forma `/c`abreviada.<br /><br /> Embora o caractere curinga (\*) possa ser usado quando você especifica os nomes do componente e da interface, é recomendável não usá-lo, pois você pode expor interfaces que não pretendiam.|  
|`/hosting:` \<*complus*  &#124; *was*\>|Especifica se o modo de hospedagem COM+ ou o modo de hospedagem da Web deve ser usado.<br /><br /> Forma `/h`abreviada.<br /><br /> Usar o modo de hospedagem COM+ requer ativação explícita do aplicativo COM+. O uso do modo de hospedagem da Web permite que o aplicativo COM+ seja ativado automaticamente conforme necessário. Se o aplicativo COM+ for um aplicativo de biblioteca, ele será executado no processo de Serviços de Informações da Internet (IIS). Se o aplicativo COM+ for um aplicativo de servidor, ele será executado no processo Dllhost. exe.|  
|`/webSite:` \<*WebsiteName*\>|Especifica o site para hospedagem quando o modo de hospedagem da Web é usado ( `/hosting` consulte o sinalizador).<br /><br /> Forma `/w`abreviada.<br /><br /> Se nenhum site da Web for especificado, o site padrão será usado.|  
|`/webDirectory:` \<*WebDirectoryName*\>|Especifica o diretório virtual para hospedagem quando a hospedagem Web é usada (consulte `/hosting` o sinalizador).<br /><br /> Forma `/d`abreviada.|  
|`/mex`|Adiciona um ponto de extremidade de serviço de intercâmbio de metadados (MEX) à configuração de serviço padrão para dar suporte a clientes que desejam recuperar uma definição de contrato do serviço.<br /><br /> Forma `/x`abreviada.|  
|`/id`|Exibe as informações de aplicativo, componente e interface como IDs.<br /><br /> Forma `/k`abreviada.|  
|`/nologo`|Impede que o ComSvcConfig. exe exiba seu logotipo.<br /><br /> Forma `/n`abreviada.|  
|`/verbose`|Gera todos os avisos ou texto informativo além dos erros encontrados.<br /><br /> Forma `/v`abreviada.|  
|`/help`|Exibe a mensagem de uso.<br /><br /> Forma `/?`abreviada.|  
|`/partial`|Gera uma configuração de serviço quando a interface especificada inclui uma ou mais assinaturas de método que podem ser expostas. No momento da inicialização do serviço, os métodos compatíveis aparecem como operações no contrato de serviço, e os métodos não compatíveis são ignorados e estão ausentes do contrato de serviço.<br /><br /> Se esse sinalizador estiver ausente, a ferramenta não gerará uma configuração de serviço quando a interface especificada incluir um ou mais métodos incompatíveis.|  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir adiciona `IFinances` a interface `ItemOrders.IFinancial` do componente (do aplicativo OnlineStore com+) ao conjunto de interfaces que são expostas como serviços Web, usando o modo de hospedagem com+. Todos os avisos serão exibidos além dos erros encontrados.  
  
### <a name="code"></a>Código  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir adiciona `IStockLevels` a interface `ItemInventory.Warehouse` do componente (do aplicativo OnlineWarehouse com+) ao conjunto de interfaces que são expostas como serviços Web, usando o modo de hospedagem da Web. O serviço Web é hospedado na Web no diretório virtual OnlineWarehouse do IIS.  
  
### <a name="code"></a>Código  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir remove `IFinances` a interface `ItemOrders.Financial` do componente (do aplicativo OnlineStore com+) do conjunto de interfaces que são expostas como serviços Web.  
  
### <a name="code"></a>Código  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir lista as interfaces hospedadas do COM+ atualmente expostas, juntamente com os detalhes de endereço e associação correspondentes, para o aplicativo OnlineStore COM+ no computador local.  
  
### <a name="code"></a>Código  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Consulte também

- [Como: Usar a ferramenta de configuração do modelo de serviço COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
