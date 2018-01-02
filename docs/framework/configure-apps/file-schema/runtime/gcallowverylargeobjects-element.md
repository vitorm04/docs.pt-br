---
title: '&lt;gcAllowVeryLargeObjects&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5db777f147e2eca7644d5b5f1a4bc18c8401ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcAllowVeryLargeObjects&gt; elemento
Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<gcAllowVeryLargeObjects > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se as matrizes que são maiores que 2 GB de tamanho total estão habilitadas em plataformas de 64 bits.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Matrizes com mais de 2 GB de tamanho total não estão habilitados. Esse é o padrão.|  
|`true`|Maiores que 2 GB de tamanho total de matrizes são habilitados em plataformas de 64 bits.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Usar esse elemento no arquivo de configuração de aplicativo permite que as matrizes que são maiores do que 2 GB de tamanho, mas não alterar outros limites de tamanho do objeto ou o tamanho da matriz:  
  
-   O número máximo de elementos em uma matriz é <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   O índice máximo em uma única dimensão é 2,147,483,591 (0x7FFFFFC7) para matrizes de bytes e matrizes de estruturas de byte único e 2,146,435,071 (0X7FEFFFFF) para outros tipos.  
  
-   O tamanho máximo de cadeias de caracteres e outros objetos de matriz não é alterado.  
  
> [!CAUTION]
>  Antes de habilitar esse recurso, certifique-se de que seu aplicativo não incluir o código não seguro que pressupõe que todas as matrizes são menores que 2 GB de tamanho. Por exemplo, o código não seguro que usa matrizes como buffers pode ser suscetível a saturações de buffer se ele está escrito na suposição de que matrizes não deve exceder 2 GB.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar esse recurso para um aplicativo.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
