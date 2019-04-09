---
title: <legacyCorruptedStateExceptionsPolicy> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 777d496614435106b84b47b9aa3d35d964bc3e07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115096"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy > elemento
Especifica se o common language runtime permite código gerenciado detecte violações de acesso e outras exceções de estado corrompido.  
  
 \<configuration>  
\<runtime>  
\<legacyCorruptedStateExceptionsPolicy>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica que o aplicativo irá capturar corrompendo falhas de exceção de estado, como violações de acesso.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O aplicativo não capturará corrompendo falhas de exceção de estado, como violações de acesso. Esse é o padrão.|  
|`true`|O aplicativo irá capturar corrompendo falhas de exceção de estado, como violações de acesso.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 3.5 e anteriores, o common language runtime permitido código gerenciado capturar exceções que foram geradas por estados de processo corrompido. Uma violação de acesso é um exemplo desse tipo de exceção.  
  
 Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]gerenciado código não captura esses tipos de exceções em `catch` blocos. No entanto, você pode substituir essa alteração e manter o tratamento de exceções de estado corrompido de duas maneiras:  
  
-   Defina as `<legacyCorruptedStateExceptionsPolicy>` do elemento `enabled` atributo `true`. Essa configuração é aplicada processwide e afeta todos os métodos.  
  
 - ou -  
  
-   Aplicar a <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> de atributo para o método que contém as exceções `catch` bloco.  
  
 Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e versões posteriores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o aplicativo deve ser revertido para o comportamento antes do [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]e detectar corrompam todas as falhas de exceção de estado.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
