---
title: '&lt;PreferComInsteadOfManagedRemoting&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9292a0973df100acbffa341d7c0ca2604455f7fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522330"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a>&lt;PreferComInsteadOfManagedRemoting&gt; elemento
Especifica se o tempo de execução usará a interoperabilidade COM em vez de comunicação remota para todas as chamadas entre limites de domínio de aplicativo.  
  
 \<configuration>  
\<runtime>  
\<PreferComInsteadOfManagedRemoting>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Indica se o tempo de execução usará a interoperabilidade COM em vez de comunicação remota entre limites de domínio de aplicativo.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução usará a comunicação remota entre limites de domínio de aplicativo. Esse é o padrão.|  
|`true`|O tempo de execução usará a interoperabilidade entre os limites de domínio de aplicativo.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Quando você define o `enabled` atributo `true`, o tempo de execução se comporta da seguinte maneira:  
  
-   O tempo de execução não chama [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) para um [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface quando um [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface entra no domínio por meio de uma interface COM. Em vez disso, ele cria um [(Runtime Callable Wrapper)](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) em torno do objeto.  
  
-   O tempo de execução retorna E_NOINTERFACE quando ele recebe um `QueryInterface` chamar para um [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface para qualquer [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) que foi criado neste domínio.  
  
 Esses dois comportamentos Certifique-se de que todas as chamadas sobre COM interfaces entre os objetos gerenciados entre o uso de limites de domínio do aplicativo COM e interoperabilidade de COM em vez de comunicação remota.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o tempo de execução deve usar COM interoperabilidade entre os limites de isolamento:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
