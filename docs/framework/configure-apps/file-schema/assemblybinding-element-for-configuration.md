---
title: '&lt;assemblyBinding&gt; elemento para &lt;configuração&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5693b92ac35a357ff1f8643d0eb9ec2105acecb4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193350"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding > elemento para \<configuration >

Especifica a diretiva de ligação de assembly no nível de configuração.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<assemblyBinding >**

## <a name="syntax"></a>Sintaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **xmlns** | Atributo obrigatório.<br><br>Especifica o namespace XML necessário para a associação de assembly. Use a cadeia de caracteres "urn: schemas-microsoft-v1" como o valor. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-element"></a>Elemento filho

|     | Descrição |
| --- | ----------- |
| [**\<linkedConfiguration >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | Especifica um arquivo de configuração a ser incluído. |

## <a name="remarks"></a>Comentários

O [  **\<linkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) elemento simplifica o gerenciamento de assemblies de componente, permitindo que os arquivos de configuração de aplicativo para incluir o assembly de arquivos de configuração locais bem conhecidos, em vez de duplicar as definições de configuração de assembly.

> [!NOTE]
> O  **\<linkedConfiguration >** elemento não tem suporte para aplicativos com manifestos do Windows lado a lado.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
