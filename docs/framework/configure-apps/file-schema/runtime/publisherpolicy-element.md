---
title: '&lt;publisherPolicy&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c81b403fa4d633428946d36960d5df32df76d21
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613772"
---
# <a name="ltpublisherpolicygt-element"></a>&lt;publisherPolicy&gt; elemento
Especifica se o tempo de execução aplica a política do editor.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<dependentAssembly >  
\<publisherPolicy >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`apply`|Especifica se deve aplicar a política do publicador.|  
  
## <a name="apply-attribute"></a>Aplicar o atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`yes`|Aplica a política de publicador. Essa é a configuração padrão.|  
|`no`|Não se aplica a política de editor.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Quando um fornecedor de componentes lança uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que os aplicativos que usam a versão antiga agora usar a nova versão. Para especificar se deseja aplicar a política de editor para um determinado assembly, coloque o  **\<publisherPolicy >** elemento no  **\<dependentAssembly >** elemento.  
  
 A configuração padrão para o **aplique** atributo é **Sim**. Definindo o **se aplicam** atributo **nenhuma** substitui qualquer anterior **Sim** configurações de um assembly.  
  
 A permissão é necessária para um aplicativo ignorar explicitamente a política de publicador usando o [ \<publisherPolicy aplicar = "no" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo. A permissão é concedida ao definir a <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission>. Para obter mais informações, consulte [permissão de segurança de redirecionamento de associação de Assembly](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desativa a política de editor para o assembly `myAssembly`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Redirecionando versões de assembly](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
