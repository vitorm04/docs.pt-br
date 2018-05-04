---
title: '&lt;shadowCopyVerifyByTimestamp&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2439a4812163562a73bd3520e65b9973e666a863
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt; elemento
Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<shadowCopyVerifyByTimestamp > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|habilitado|Atributo obrigatório.<br /><br /> Especifica se os domínios de aplicativos que usam a cópia de sombra comparam os carimbos de hora do assembly ao iniciar, para determinar se um assembly foi atualizado antes do conjunto de cópias de sombra.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Na inicialização, copia apenas os assemblies que foram atualizados desde a última foram copiados para o diretório de cópia de sombra. Esse é o padrão para o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que era copiar todos os arquivos na inicialização.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], os assemblies são copiados somente se seus carimbos de data / hora indicar que foram alteradas desde a última foram copiados para o diretório de cópia de sombra de sombra. Isso melhora o tempo de inicialização para muitos aplicativos que usam a cópia de sombra, conforme descrito em [cópia de sombra de Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Aplicativos que têm uma porcentagem alta e a frequência de atualizações do assembly não podem se beneficiar dessa alteração no comportamento. Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão de cópia de sombra no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Cópias de sombra de assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
