---
title: Elemento <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 45052d99bb297ac39d058fa405fe57a7c991f738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151344"
---
# <a name="crst_disablespinwait-element"></a>Elemento \<Crst_DisableSpinWait>

Especifica se é para desabilitar a espera de rotação para uma seção crítica quando contendeda.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**habilitado**|Especifica se a rotação-aguardando seções críticas quando elas são contendedas está desabilitada.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|1|Desabilitar giro-aguardando quando uma seção crítica não puder ser adquirida.|  
|0|Não desabilite o giro-aguardando quando uma seção crítica não puder ser adquirida. Esse é o valor padrão.|  
  
### <a name="child-elements"></a>Elementos filho  

 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre várias definições de configuração de tempo de execução.|  
  
## <a name="example"></a>Exemplo  

O exemplo a seguir desabilita a espera de rotação em seções críticas quando contendeda.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema do arquivo de configuração](../index.md)
