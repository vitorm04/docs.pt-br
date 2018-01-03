---
title: '&lt;remover&gt; elemento para &lt;configSections&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf2cb49fbeb01ad176a1d24d711cebc97ba14004
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-configsections"></a>\<Remover > elemento \<configSections >

Remove uma seção predefinida ou grupo de seção.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Remover >**

## <a name="syntax"></a>Sintaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome da seção ou grupo da seção para remover. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configSections >** elemento](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contém declarações de namespace e de seção de configuração. |

# <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Você pode usar o  **\<remover >** elemento remover seções e grupos de seções do seu aplicativo que foram definidas em um nível superior na hierarquia de arquivos de configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar o  **\<remover >** elemento em um arquivo de configuração do aplicativo para remover uma seção definida anteriormente no arquivo de configuração da máquina.

O seguinte código de arquivo de configuração de máquina declara a seção  **\<sampleSection >**:

```xml
<!-- Machine.config file -->
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

O seguinte código de arquivo de configuração de aplicativo remove o  **\<sampleSection >** seção. Após a remoção, o aplicativo não é possível recuperar as configurações no  **\<sampleSection >**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
