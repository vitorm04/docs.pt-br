---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927664"
---
# <a name="configsections-element-for-configuration"></a>\<configSections > elemento para \<a configuração >

Contém as declarações de namespace e seção de configuração.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<configSections>**

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [ **\<> da seção**](section-element.md) | Contém uma declaração de seção de configuração. |
| [ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |
| [ **\<remove>** ](remove-element-for-configsections.md) | Remove uma seção ou um grupo de seções predefinido. |
| [ **\<clear>** ](clear-element-for-configsections.md) | Limpa todas as seções e grupos de seções definidos anteriormente. |

## <a name="remarks"></a>Comentários

Se esse elemento estiver em um arquivo de configuração, ele deverá ser o primeiro elemento filho do  **\<elemento Configuration >** .

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
