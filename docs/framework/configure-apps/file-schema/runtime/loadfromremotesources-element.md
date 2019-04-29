---
title: Elemento <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704590"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources > elemento
Especifica se os assemblies carregados de fontes remotas devem receber confiança total no .NET Framework 4 e posterior.
  
> [!NOTE]
>  Caso tenha sido direcionado para este artigo devido a uma mensagem de erro na lista de erros do projeto do Visual Studio ou um erro de compilação, consulte [como: Usar um Assembly da Web no Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
 \<configuration>  
\<runtime>  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se um assembly que é carregado de uma fonte remota deve receber confiança total.|  
  
## <a name="enabled-attribute"></a>atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não conceda confiança total para aplicativos de fontes remotas. Esse é o padrão.|  
|`true`|Conceder confiança total para aplicativos de fontes remotas.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários

No .NET Framework 3.5 e versões anteriores, se você carregar um assembly de um local remoto, o código no assembly é executado em confiança parcial com um conjunto de concessões que depende da zona da qual ele é carregado. Por exemplo, se você carregar um assembly de um site, ele é carregado na zona da Internet e concedeu o conjunto de permissões de Internet. Em outras palavras, ele executa em uma área de segurança de Internet.

Começando com o .NET Framework 4, a política de CAS (segurança) de acesso do código está desabilitada e os assemblies são carregados em confiança total. Normalmente, isso seria conceder confiança total para os assemblies carregados com o <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> método que anteriormente havia sido em área restrita. Para evitar isso, a capacidade de executar o código em assemblies carregados de uma fonte remota está desabilitada por padrão. Por padrão, se você tentar carregar um assembly remoto, um <xref:System.IO.FileLoadException> com uma mensagem de exceção, como o seguinte é gerado:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Para carregar o assembly e executar seu código, você deve:

- Criar explicitamente uma área restrita para o assembly (consulte [como: Executar código parcialmente confiável em uma área restrita](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Execute o código do assembly em confiança total. Você pode fazer isso configurando a `<loadFromRemoteSources>` elemento. Ele permite que você especifique os assemblies que são executados em confiança parcial em versões anteriores do .NET Framework agora executar em confiança total no .NET Framework 4 e versões posteriores.

> [!IMPORTANT]
> Se o assembly não deve ser executado em confiança total, não defina este elemento de configuração. Em vez disso, crie uma área restrita e <xref:System.AppDomain> no qual carregar o assembly.

O `enabled` de atributo para o `<loadFromRemoteSources>` elemento é eficaz apenas quando a segurança de acesso do código (CAS) está desabilitada. Por padrão, a política de CAS está desabilitada no .NET Framework 4 e versões posteriores. Se você definir `enabled` para `true`, assemblies remotos recebem confiança total.

Se `enabled` não está definido como `true`, um <xref:System.IO.FileLoadException> é lançada sob a qualquer uma das seguintes condições:

- O comportamento de modo seguro do domínio atual é diferente de seu comportamento no .NET Framework 3.5. Isso requer a política de CAS seja desabilitado e o domínio atual não devem ser em área restrita.

- O assembly que está sendo carregado não é do `MyComputer` zona.

Definindo o `<loadFromRemoteSources>` elemento para `true` impede essa exceção de que está sendo gerada. Ele permite que você especifique que você não depender do common language runtime para a área restrita os assemblies carregados para a segurança e que pode ser permitidos para execução no total confiança.

## <a name="notes"></a>Observações

- No .NET Framework 4.5 e versões posteriores, os assemblies em compartilhamentos de rede local são executados em confiança total por padrão. Você não precisa habilitar o `<loadFromRemoteSources>` elemento.

- Se um aplicativo tiver sido copiado da web, ele será sinalizado pelo Windows como sendo um aplicativo web, mesmo que ele reside no computador local. Você pode alterar essa designação alterando suas propriedades de arquivo, ou você pode usar o `<loadFromRemoteSources>` confiança total do elemento para conceder o conjunto. Como alternativa, você pode usar o <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> método para carregar um assembly local que o sistema operacional foi sinalizada como tendo sido carregados da web.

- Você pode obter um <xref:System.IO.FileLoadException> em um aplicativo que está em execução em um aplicativo do Windows Virtual PC. Isso pode acontecer quando você tenta carregar um arquivo de pastas vinculadas no computador de hospedagem. Ele também pode ocorrer quando você tenta carregar um arquivo de uma pasta vinculada ao longo [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (serviços de Terminal). Para evitar a exceção, defina `enabled` para `true`.

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto. Para obter mais informações, consulte o artigo [mais implícita usa da política de CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) no blog de segurança do .NET.  

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como conceder confiança total para os assemblies carregados de fontes remotas.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Consulte também

- [Usos mais implícitos da política de CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [Como: Executar o código parcialmente confiável em uma área restrita](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
