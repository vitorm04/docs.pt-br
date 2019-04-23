---
title: Elemento <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba411114bfb853e06c83adb42713d43f1452d9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135058"
---
# <a name="etwenable-element"></a>\<etwEnable > elemento
Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<etwEnabled>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|habilitado|Atributo obrigatório.<br /><br /> Especifica se o ETW deve ser habilitado.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Habilite o ETW. Esse é o padrão para as versões de sistemas operacionais do Windows Vista e Windows Server 2008 a partir do Windows.|  
|false|Desabilite o ETW. Esse é o padrão para versões anteriores do Windows.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o Windows Vista, o ETW é habilitado por padrão. Use esse elemento para desabilitar o ETW para um aplicativo. Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.  
  
> [!NOTE]
>  ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração do registro. Ver [controlando o log do .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Controlando o log no .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
