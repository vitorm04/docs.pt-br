---
title: Elemento <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154121"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects> Element
Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se os arrays com maior duração de 2 GB no tamanho total estão habilitados em plataformas de 64 bits.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Matrizes maiores que 2 GB em tamanho total não estão habilitadas. Esse é o padrão.|  
|`true`|Matrizes maiores que 2 GB em tamanho total são habilitadas em plataformas de 64 bits.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
  
## <a name="remarks"></a>Comentários  
 O uso desse elemento no arquivo de configuração do aplicativo permite matrizes com tamanho superior a 2 GB, mas não altera outros limites no tamanho do objeto ou tamanho do array:  
  
- O número máximo de elementos em uma matriz é <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
- O índice máximo em qualquer dimensão é de 2.147.483.591 (0x7FFFFFC7) para matrizes de bytes e matrizes de estruturas de byte único, e 2.146.435.071 (0X7FEFFFFF) para outros tipos.  
  
- O tamanho máximo para strings e outros objetos não-array é inalterado.  
  
> [!CAUTION]
> Antes de habilitar esse recurso, certifique-se de que seu aplicativo não inclua código inseguro que pressupõe que todas as matrizes sejam menores que 2 GB de tamanho. Por exemplo, o código inseguro que usa arrays como buffers pode ser suscetível a buffer saqueados se for escrito na suposição de que os arrays não excederão 2 GB.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como ativar esse recurso para um aplicativo.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>Com suporte em

.NET Framework 4.5 e versões posteriores

## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
