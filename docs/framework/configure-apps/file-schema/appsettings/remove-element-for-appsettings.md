---
title: '&lt;remover&gt; elemento para &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 21fedf064596979dbfb4190d9956da616295af3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752111"
---
# <a name="remove-element-for-appsettings"></a>\<Remover > elemento \<appSettings >

Remove as configurações de aplicativo personalizado.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Remover >**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atributo

|         | Descrição |
| ------- | ----------- |
| **key** | Atributo obrigatório.<br><br>Especifica o nome da chave a ser removido. |

### <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
