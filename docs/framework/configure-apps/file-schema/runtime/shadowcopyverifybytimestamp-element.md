---
title: Elemento <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1815da141beb3dd1022fe1a74f872aa70b4ded43
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456349"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<Elemento shadowCopyVerifyByTimestamp>
Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<Elemento shadowCopyVerifyByTimestamp>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|habilitado|Atributo obrigatório.<br /><br /> Especifica se os domínios de aplicativos que usam a cópia de sombra comparam carimbos de data / hora do assembly ao iniciar, para determinar se um assembly foi atualizado antes do conjunto de cópias de sombra.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Na inicialização, copia apenas os assemblies tenham sido atualizados desde a última foram copiados para o diretório de cópia de sombra. Esse é o padrão para o .NET Framework 4.|  
|false|Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que foi copiar todos os arquivos na inicialização.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 4, os assemblies são apenas se seus carimbos de data / hora que indicam que eles foram alterados desde que eles pela última vez foram copiados para o diretório de cópia de sombra de cópia de sombra. Isso melhora os tempos de inicialização para muitos aplicativos que usam a cópia de sombra, conforme descrito em [cópias de sombra de Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Aplicativos que têm um alto percentual e uma frequência de atualizações do assembly não podem se beneficiar dessa mudança no comportamento. Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão de no .NET Framework 4 a cópia de sombra e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Cópias de sombra de assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
