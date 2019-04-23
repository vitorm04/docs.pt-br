---
title: Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158644"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
A ferramenta de linha de comando de configuração de modelo de serviço COM+ (ComSvcConfig.exe) permite que você configure interfaces COM+ deve ser exposta como serviços da Web.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Você deve ser um administrador no computador local para usar ComSvcConfig.exe.  
  
 A ferramenta pode ser encontrada no seguinte local  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Para obter mais informações sobre ComSvcConfig.exe, consulte [como: Use a ferramenta de configuração de modelo de serviço COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 A tabela a seguir descreve os modos que podem ser usados com ComSvcConfig.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`install`|Instala uma configuração para uma interface COM+ para integração com o modelo de serviço.<br /><br /> Forma abreviada `/i`.|  
|`uninstall`|Desinstala uma configuração para uma interface COM+ de integração do modelo de serviço.<br /><br /> Forma abreviada `/u`.|  
|`list`|Lista informações sobre aplicativos COM+ e componentes com interfaces que estão configuradas para integração com o modelo de serviço.<br /><br /> Forma abreviada `/l`.|  
  
 A tabela a seguir descreve os sinalizadores que podem ser usados com ComSvcConfig.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/application:` \<*ApplicationID* &#124; *ApplicationName*\>|Especifica o aplicativo COM+ para configurar.<br /><br /> Forma abreviada `/a`.|  
|`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\>|Especifica o componente COM+ e a interface que será configurado como o contrato do serviço.<br /><br /> Forma abreviada `/c`.<br /><br /> Embora o caractere curinga (\*) pode ser usado quando você especifica os nomes de componente e a interface, é recomendável que você não usá-lo, porque você pode expor interfaces que você não pretendia.|  
|`/hosting:` \<*complus*  &#124; *was*\>|Especifica se deve usar o modo ou o modo de hospedagem da Web de hospedagem COM+.<br /><br /> Forma abreviada `/h`.<br /><br /> Modo de hospedagem usando o COM+ exige a ativação explícita do aplicativo COM+. Usando a Web do modo de hospedagem permite que o aplicativo COM+ a ser ativado automaticamente como necessário. Se o aplicativo COM+ é um aplicativo de biblioteca, ele é executado no processo de serviços de informações da Internet (IIS). Se o aplicativo COM+ é um aplicativo de servidor, ele é executado no processo de Dllhost.exe.|  
|`/webSite:` \<*WebsiteName*\>|Especifica o site da Web para hospedar quando o modo de hospedagem na Web é usado (consulte a `/hosting` sinalizador).<br /><br /> Forma abreviada `/w`.<br /><br /> Se nenhum site da Web for especificado, o site padrão será usado.|  
|`/webDirectory:` \<*WebDirectoryName*\>|Especifica o diretório virtual para a hospedagem de hospedagem na Web é usado (consulte a `/hosting` sinalizador).<br /><br /> Forma abreviada `/d`.|  
|`/mex`|Adiciona um ponto de extremidade de serviço de troca de metadados (MEX) à configuração de serviço padrão para dar suporte a clientes que desejam recuperar uma definição de contrato de serviço.<br /><br /> Forma abreviada `/x`.|  
|`/id`|Exibe o aplicativo, componente e informações de interface, como IDs.<br /><br /> Forma abreviada `/k`.|  
|`/nologo`|Impede que ComSvcConfig.exe exibindo seu logotipo.<br /><br /> Forma abreviada `/n`.|  
|`/verbose`|Gera todos os avisos ou texto informativo, além de todos os erros encontrados.<br /><br /> Forma abreviada `/v`.|  
|`/help`|Exibe a mensagem de uso.<br /><br /> Forma abreviada `/?`.|  
|`/partial`|Gera uma configuração de serviço quando a interface especificada inclui uma ou mais assinaturas de método que podem ser expostas. No momento da inicialização de serviço, métodos compatíveis aparecem como operações no contrato de serviço, e não-compatíveis com métodos são ignorados e estavam ausentes ao contrato de serviço.<br /><br /> Se esse sinalizador estiver ausente, a ferramenta não irá gerar uma configuração de serviço quando a interface especificada inclui um ou mais métodos incompatíveis.|  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir adiciona o `IFinances` interface da `ItemOrders.IFinancial` componente (do aplicativo aplicativo OnlineStore COM+) ao conjunto de interfaces que são expostas como serviços da Web, usando o modo de hospedagem COM+. Todos os avisos serão gerados, além de todos os erros encontrados.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir adiciona o `IStockLevels` interface da `ItemInventory.Warehouse` componente (a partir do aplicativo OnlineWarehouse COM+) ao conjunto de interfaces que são expostos como serviços Web, usando o modo de host Web. O serviço Web é que Web hospedada no diretório virtual OnlineWarehouse do IIS.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir remove a `IFinances` interface da `ItemOrders.Financial` componente (do aplicativo OnlineStore COM+ aplicativo) do conjunto de interfaces que são expostas como serviços da Web.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Descrição  
 A exemplo a seguir lista expostos atualmente hospedado interfaces COM+, juntamente com o endereço de correspondência e os detalhes da associação, para o aplicativo do aplicativo OnlineStore COM+ no computador local.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Consulte também

- [Como: Use a ferramenta de configuração de modelo de serviço COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
