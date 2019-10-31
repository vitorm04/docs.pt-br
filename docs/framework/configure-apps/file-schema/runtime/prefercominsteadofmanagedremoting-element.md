---
title: Elemento <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 47c568a8d6e89a195414552b3db5953ee61d1e55
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116011"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<elemento de > PreferComInsteadOfManagedRemoting
Especifica se o tempo de execução usará a interoperabilidade COM em vez de comunicação remota para todas as chamadas entre limites de domínio do aplicativo.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Indica se o tempo de execução usará a interoperabilidade COM em vez da comunicação remota entre os limites do domínio do aplicativo.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução usará a comunicação remota entre os limites do domínio do aplicativo. Esse é o padrão.|  
|`true`|O tempo de execução usará a interoperabilidade COM entre limites de domínio do aplicativo.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Quando você define o atributo `enabled` como `true`, o tempo de execução se comporta da seguinte maneira:  
  
- O tempo de execução não chama [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) para uma interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) quando uma interface [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) entra no domínio por meio de uma interface com. Em vez disso, ele constrói um RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) em volta do objeto.  
  
- O tempo de execução retorna E_NOINTERFACE quando recebe uma chamada de `QueryInterface` para uma interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) para qualquer CCW ( [com callable wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) que tenha sido criado nesse domínio.  
  
 Esses dois comportamentos garantem que todas as chamadas sobre interfaces COM entre objetos gerenciados entre os limites de domínio do aplicativo usem a interoperabilidade com e COM em vez de comunicação remota.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o tempo de execução deve usar a interoperabilidade COM entre limites de isolamento:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
