---
title: Elemento <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154056"
---
# <a name="loadfromremotesources-element"></a>\<carregarDeelemento>Defontes remotas
Especifica se os conjuntos carregados de fontes remotas devem ser concedidos total confiança no Quadro .NET 4 e posterior.
  
> [!NOTE]
> Se você foi direcionado a este artigo por causa de uma mensagem de erro na lista de erros do projeto Visual Studio ou de um erro de compilação, consulte [Como: Usar um conjunto da Web no Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<carregamentoDeDeFormaremotas>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se um conjunto carregado de uma fonte remota deve ser concedido total confiança.|  
  
## <a name="enabled-attribute"></a>atributo ativado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não conceda total confiança a aplicações de fontes remotas. Esse é o padrão.|  
|`true`|Conceda total confiança a aplicações de fontes remotas.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
  
## <a name="remarks"></a>Comentários

Nas versões .NET Framework 3.5 e anteriores, se você carregar um conjunto de um local remoto, o código no conjunto será executado em confiança parcial com um conjunto de concessões que depende da região da qual ele é carregado. Por exemplo, se você carregar um conjunto de um site, ele é carregado na região da Internet e concedido o conjunto de permissões da Internet. Em outras palavras, ele é executado em uma caixa de areia da Internet.

Começando com o .NET Framework 4, a política CAS (Code Access Security, segurança de acesso ao código) é desativada e as montagens são carregadas em total confiança. Normalmente, isso concederia total confiança às <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> assembléias carregadas com o método que anteriormente havia sido sandboxed. Para evitar isso, a capacidade de executar código em conjuntos carregados de uma fonte remota é desativada por padrão. Por padrão, se você tentar carregar <xref:System.IO.FileLoadException> um conjunto remoto, uma mensagem com exceção como a seguinte será lançada:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

Para carregar o conjunto e executar seu código, você deve:

- Crie explicitamente uma caixa de areia para o conjunto (veja [Como: Executar código parcialmente confiável em uma caixa de areia](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Execute o código da assembléia em total confiança. Você faz isso configurando o `<loadFromRemoteSources>` elemento. Ele permite especificar que as assembléias que são executadas em confiança parcial em versões anteriores do .NET Framework agora são executadas em total confiança nas versões .NET Framework 4 e posteriores.

> [!IMPORTANT]
> Se o conjunto não for executado em plena confiança, não defina este elemento de configuração. Em vez disso, crie <xref:System.AppDomain> uma caixa de areia na qual para carregar o conjunto.

O `enabled` atributo `<loadFromRemoteSources>` para o elemento só é eficaz quando o CAS (Code Access Security, segurança de acesso ao código) é desativado. Por padrão, a diretiva CAS é desativada nas versões .NET Framework 4 e posteriores. Se você `enabled` `true`definir para , assembléias remotas são concedidas total confiança.

Se `enabled` não for `true`definido <xref:System.IO.FileLoadException> para, a é jogado qualquer uma das seguintes condições:

- O comportamento de sandboxing do domínio atual é diferente de seu comportamento no Quadro .NET 3.5. Isso exige que a política CAS seja desativada e que o domínio atual não seja sandbox.

- A montagem que está sendo `MyComputer` carregada não é da zona.

Definir `<loadFromRemoteSources>` o `true` elemento para evitar que essa exceção seja lançada. Ele permite que você especifique que você não está confiando no tempo de execução do idioma comum para sandbox os conjuntos carregados para segurança, e que eles podem ser autorizados a executar em total confiança.

## <a name="notes"></a>Observações

- Nas versões .NET Framework 4.5 e posteriores, as assembléias sobre ações de rede locais são executadas em total confiança por padrão; você não precisa ativar `<loadFromRemoteSources>` o elemento.

- Se um aplicativo foi copiado da web, ele é sinalizado pelo Windows como sendo um aplicativo web, mesmo que resida no computador local. Você pode alterar essa designação alterando suas `<loadFromRemoteSources>` propriedades de arquivo, ou você pode usar o elemento para conceder a total confiança da assembléia. Como alternativa, você pode <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> usar o método para carregar um conjunto local que o sistema operacional sinalizou como tendo sido carregado da web.

- Você pode <xref:System.IO.FileLoadException> obter um em um aplicativo que está sendo executado em um aplicativo de PC virtual do Windows. Isso pode acontecer quando você tenta carregar um arquivo de pastas vinculadas no computador de hospedagem. Também pode ocorrer quando você tenta carregar um arquivo de uma pasta vinculada sobre [serviços de área de trabalho remota](/windows/win32/termserv/terminal-services-portal) (Serviços de Terminal). Para evitar a `enabled` exceção, definido como `true`.

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto. Para obter mais informações, consulte o artigo [Usos mais implícitos da política CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) no blog .NET Security.  

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como conceder confiança total a assembléias carregadas de fontes remotas.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Confira também

- [Usos mais implícitos da política CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [Como executar código parcialmente confiável em uma área restrita](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
