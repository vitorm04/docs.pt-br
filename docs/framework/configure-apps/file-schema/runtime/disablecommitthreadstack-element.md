---
title: '&lt;disableCommitThreadStack&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d74566b71501cf21081ac894048bb1c29e0ad94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablecommitthreadstackgt-element"></a>&lt;disableCommitThreadStack&gt; elemento
Especifica se a pilha do thread completo é confirmada quando um thread é iniciado.  
  
 \<configuration>  
\<tempo de execução >  
\<disableCommitThreadStack >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Habilitado|Atributo obrigatório.<br /><br /> Especifica se a confirmação a pilha do thread completa na inicialização do thread (o comportamento padrão) está desabilitado.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Não desabilite o comportamento padrão do common language runtime, que é confirmar a pilha do thread completo quando um thread é iniciado.|  
|1|Desabilite o comportamento padrão do common language runtime, que é confirmar a pilha do thread completo quando um thread é iniciado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 É o comportamento padrão do common language runtime confirmar a pilha do thread completo quando um thread é iniciado. Se um grande número de threads deve ser criado em um servidor que tem memória limitada, e a maioria desses threads usará muito pouco espaço de pilha, o servidor pode executar melhor se o common language runtime não confirma a pilha do thread completo imediatamente quando um thread é st arted.  
  
> [!NOTE]
>  Os hosts gerenciados podem usar o `STARTUP_DISABLE_COMMITTHREADSTACK` sinalizador de inicialização no [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração para obter o mesmo resultado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar o comportamento padrão do common language runtime, que é preciso confirmar a pilha do thread completa na inicialização do thread.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
