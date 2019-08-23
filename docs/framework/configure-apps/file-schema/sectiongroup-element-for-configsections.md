---
title: Elemento <sectionGroup> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4e28e8ccea1090e6a5704b541e09dc11681278ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920646"
---
# <a name="sectiongroup-element-for-configsections"></a>\<elemento de > de seção \<para configSections >

Define um namespace para seções de configuração.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**

## <a name="syntax"></a>Sintaxe

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome do grupo de seções que você está definindo. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [configSections > elemento  **\<** ](configsections-element-for-configuration.md) | Contém as declarações de namespace e seção de configuração. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [ **\<> da seção**](section-element.md) | Contém uma declaração de seção de configuração. |

## <a name="remarks"></a>Comentários

Declarar um grupo de seções cria uma marca de contêiner para seções de configuração e garante que não haja conflitos de nomenclatura com seções de configuração definidas por outra pessoa. Você pode aninhar  **\<** elementos de > de seção entre si.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como declarar um grupo de seções e declarar seções dentro de um grupo de seções:

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
