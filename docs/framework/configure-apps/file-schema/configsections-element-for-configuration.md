---
title: '&lt;configSections&gt; elemento para &lt;configuração&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 33406a67389cdf857fa5030e20d8a4dec7662741
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="configsections-element-for-configuration"></a>\<configSections > elemento \<Configuração >

Contém declarações de namespace e de seção de configuração.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<configSections >**

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<seção >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Contém uma declaração de seção de configuração. |
| [**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Remove uma seção predefinida ou grupo de seção. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Limpa todas as seções definidas anteriormente e grupos de seções. |

## <a name="remarks"></a>Comentários

Se esse elemento estiver em um arquivo de configuração, ele deve ser o primeiro elemento filho do  **\<Configuração >** elemento.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração e definir configurações para essa seção:

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

Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
