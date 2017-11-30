---
title: "Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f812beea611633fe1fa47ced5db46c462443f28
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
A ferramenta de linha de comando de configuração de modelo de serviço COM+ (ComSvcConfig.exe) permite que você configure COM+ interfaces a serem expostas como serviços da Web.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Você deve ser um administrador no computador local para usar ComSvcConfig.exe.  
  
 A ferramenta pode ser encontrada no seguinte local  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ de comunicação  
  
 Para obter mais informações sobre ComSvcConfig.exe, consulte [como: usar a ferramenta Configuração do modelo de COM+ serviço](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 A tabela a seguir descreve os modos que podem ser usados com ComSvcConfig.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`install`|Instala uma configuração para uma interface para integração com o modelo de serviço COM+.<br /><br /> Forma abreviada `/i`.|  
|`uninstall`|Desinstala uma configuração para uma interface COM+ de integração de modelo de serviço.<br /><br /> Forma abreviada `/u`.|  
|`list`|Lista informações sobre aplicativos e componentes que têm interfaces que estão configurados para integração com o modelo de serviço.<br /><br /> Forma abreviada `/l`.|  
  
 A tabela a seguir descreve os sinalizadores que podem ser usados com ComSvcConfig.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/application:`\< *ApplicationID* &#124; *ApplicationName*\>|Especifica o aplicativo COM+ a configurar.<br /><br /> Forma abreviada `/a`.|  
|`/contract:`\< *ClassID* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124;\*\>|Especifica o componente COM+ e a interface que será configurado como o contrato para o serviço.<br /><br /> Forma abreviada `/c`.<br /><br /> Embora o caractere curinga (\*) pode ser usado quando você especificar os nomes de componente e interface, recomendamos que você não usá-lo, porque você poderá expor interfaces que você não pretendia.|  
|`/hosting:`\< *complus* &#124; *foi*\>|Especifica se deve usar o modo ou o modo de hospedagem da Web de hospedagem COM+.<br /><br /> Forma abreviada `/h`.<br /><br /> Usando o COM+ hospedar modo exige a ativação explícita do aplicativo COM+. Usar o modo de hospedagem permite que o aplicativo COM+ seja ativado automaticamente como Web necessária. Se o aplicativo COM+ é um aplicativo de biblioteca, ele é executado no processo do Internet Information Services (IIS). Se o aplicativo COM+ é um aplicativo de servidor, ele é executado no processo Dllhost.exe.|  
|`/webSite:`\< *WebsiteName*\>|Especifica o site da Web para hospedar quando o modo de hospedagem na Web é usado (consulte o `/hosting` sinalizador).<br /><br /> Forma abreviada `/w`.<br /><br /> Se nenhum site é especificado, o site padrão será usado.|  
|`/webDirectory:`\< *WebDirectoryName*\>|Especifica o diretório virtual para hospedagem de hospedagem na Web é usada (consulte o `/hosting` sinalizador).<br /><br /> Forma abreviada `/d`.|  
|`/mex`|Adiciona um ponto de extremidade do serviço de troca de metadados (MEX) para a configuração de serviço padrão para oferecer suporte a clientes que deseja recuperar de uma definição de contrato do serviço.<br /><br /> Forma abreviada `/x`.|  
|`/id`|Exibe o aplicativo, componente e informações de interface como IDs.<br /><br /> Forma abreviada `/k`.|  
|`/nologo`|Impede que ComSvcConfig.exe seu logotipo.<br /><br /> Forma abreviada `/n`.|  
|`/verbose`|Gera todos os avisos ou texto informativo, além de todos os erros encontrados.<br /><br /> Forma abreviada `/v`.|  
|`/help`|Exibe a mensagem de uso.<br /><br /> Forma abreviada `/?`.|  
|`/partial`|Gera uma configuração de serviço quando a interface especificada inclui uma ou mais assinaturas de método que podem ser expostas. No momento da inicialização de serviço, métodos compatíveis aparecem como operações no contrato de serviço, e os métodos de não compatível são ignorados e ausentes ao contrato de serviço.<br /><br /> Se esse sinalizador estiver ausente, a ferramenta não gerará uma configuração de serviço quando a interface especificada inclui um ou mais métodos incompatíveis.|  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir adiciona o `IFinances` interface do `ItemOrders.IFinancial` componente (a partir do aplicativo COM+ OnlineStore) para o conjunto de interfaces que são expostas como serviços da Web, usando o modo de hospedagem COM+. Todos os avisos serão gerados além de todos os erros encontrados.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir adiciona o `IStockLevels` interface do `ItemInventory.Warehouse` componente (a partir do aplicativo COM+ OnlineWarehouse) para o conjunto de interfaces que são expostas como serviços da Web, usando o modo de hospedagem na Web. O serviço Web é que Web hospedada no diretório virtual OnlineWarehouse do IIS.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir remove o `IFinances` interface do `ItemOrders.Financial` componente (a partir do aplicativo COM+ OnlineStore) do conjunto de interfaces que são expostas como serviços da Web.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Descrição  
 A exemplo a seguir lista atualmente expostos hospedados pelo COM+ interfaces, juntamente com o endereço correspondente e os detalhes de associação, para o aplicativo COM+ OnlineStore no computador local.  
  
### <a name="code"></a>Código  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como: usar a ferramenta de configuração de modelo de serviço COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
