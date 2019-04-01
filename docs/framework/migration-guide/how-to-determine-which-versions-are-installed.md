---
title: 'Como: Determinar quais versões do .NET Framework estão instaladas'
ms.date: 03/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c4ad3ca5694457637a82a36c8db4534df43a9d7
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504425"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Como: Determinar quais versões do .NET Framework estão instaladas

Os usuários podem [instalar](https://docs.microsoft.com/dotnet/framework/install) e executar várias versões do .NET Framework em seus computadores. Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário. 

O .NET Framework consiste em dois componentes principais, que têm o controle de versão feito separadamente:  
  
- Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos. O .NET Framework e assemblies que compartilham o mesmo número de versão.  
  
- O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos. O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).  

> [!NOTE]
> Cada nova versão do .NET Framework retém recursos de versões anteriores e adiciona novos recursos. Você pode carregar várias versões do .NET Framework em um único computador ao mesmo tempo, o que significa que você pode instalar o .NET Framework sem precisar desinstalar as versões anteriores. Em geral, você não deve desinstalar as versões anteriores do .NET Framework, porque um aplicativo que você usa pode depender de uma versão específica e pode ser interrompido caso essa versão seja removida.
>
> Há uma diferença entre a versão do .NET Framework e a versão do CLR: 
> - A versão do .NET Framework baseia-se no conjunto de assemblies que forma a biblioteca de classes .NET Framework. Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2. 
>- A versão do CLR baseia-se no tempo de execução no qual os aplicativos .NET Framework são executados. Uma única versão do CLR geralmente dá suporte a várias versões do .NET Framework. Por exemplo, o CLR versão 4.0.30319.*xxxxx* dá suporte ao .NET Framework versões 4 a 4.5.2; o CLR versão 4.0.30319.42000 dá suporte a versões do .NET Framework que começam no .NET Framework 4.6. 
>
> Para obter mais informações sobre as versões, confira [Versões e dependências do .NET Framework](versions-and-dependencies.md).


Para obter uma lista das versões do .NET Framework instaladas em um computador, acesse o Registro. Use o Editor do Registro para exibir o Registro ou use o código para consultá-lo:
 
- Encontre versões mais recentes do .NET Framework (4.5 e posterior): 
     - [Usar o Editor do Registro para encontrar versões do .NET Framework](#net_b)  
     - [Usar o código para consultar versões do .NET Framework no Registro](#net_d)  
     - [Usar o PowerShell para consultar versões do .NET Framework no Registro](#ps_a)
- Encontre versões mais antigas do .NET Framework (1&#8211;4):
     - [Usar o Editor do Registro para encontrar versões do .NET Framework](#net_a)
     - [Usar o código para consultar versões do .NET Framework no Registro](#net_c)   

Para obter uma lista das versões do CLR instaladas em um computador, use uma ferramenta ou o código:  
  
- [Usar a ferramenta Clrver](#clr_a)  
- [Usar o código para consultar a classe Environment](#clr_b)  

Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, confira [Como: Determinar quais atualizações do .NET Framework estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md). 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a>Encontrar versões mais recentes do .NET Framework (4.5 e posterior)

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Encontrar versões 4.5 do .NET Framework no Registro

1. No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.

     Você precisará ter credenciais administrativas para executar o REGEDIT.

2. No Editor do Registro, abrir a seguinte subchave: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. Se a subchave **Full** não estiver presente, você não terá o .NET Framework 4.5 ou posterior instalado.

    > [!NOTE]
    > A pasta **NET Framework Setup** no Registro não começa com um ponto.

3. Verifique se há uma entrada DWORD chamada **Release**. Se ela existir, você terá o .NET Framework 4.5 ou posterior instalado. Seu valor é uma chave de versão que corresponde a uma versão específica do .NET Framework. Na figura a seguir, por exemplo, o valor da entrada **Release** é *378389*, que é a chave de versão do .NET Framework 4.5. 

     ![Entrada do Registro para o .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")

A tabela a seguir lista o valor mínimo da entrada **Release** para cada versão do .NET Framework. Use esses valores da seguinte maneira:

- Para determinar se uma versão mínima do .NET Framework está presente, teste se o valor DWORD **Release** encontrado no Registro é *superior ou igual* ao valor listado na tabela. Por exemplo, se o aplicativo exigir o .NET Framework 4.7 ou posterior, você testará um valor de chave de versão mínima igual a *460798*.

- Para testar várias versões, comece com a versão mais recente do .NET Framework e, em seguida, teste cada versão anterior sucessiva.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Versão do .NET Framework|Valor da liberação de DWORD|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

Para ver uma tabela completa de chaves de versão para o .NET Framework para versões específicas do sistema operacional Windows, consulte [Chaves de versão do .NET Framework e versões do sistema operacional Windows](release-keys-and-os-versions.md).


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a>Encontrar versões 4.5 e posteriores do .NET Framework com código

1. Use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** no Registro do Windows.

    A existência da entrada DWORD **Release** na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** indica que o .NET Framework 4.5 ou posterior está instalado em um computador. 

2. Verifique o valor da entrada **Release** para determinar a versão instalada. Para compatibilidade com a versão atual, verifique se há um valor superior ou igual ao valor listado na [tabela de versões do .NET Framework](#version_table).

O seguinte exemplo verifica o valor da entrada **Release** no Registro para encontrar o .NET Framework 4.5 e versões posteriores que estão instaladas:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Este exemplo segue a prática recomendada para a verificação de versão:

- Ele verifica se o valor da entrada **Release** é *superior ou igual* ao valor das chaves de versão conhecidas.

- Ele verifica na ordem da versão mais recente para a versão mais antiga.

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Verificar se há uma versão mínima necessária do .NET Framework (4.5 e posterior) com o PowerShell

- Use comandos do PowerShell para verificar o valor da entrada **Release** da subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.

Os exemplos a seguir verificam o valor da entrada **Release** para determinar se o .NET Framework 4.6.2 ou posterior está instalado. Esse código retornará `True` se ele estiver instalado; caso contrário, retornará `False`.

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Para verificar se há uma versão mínima necessária do .NET Framework, substitua *394802* nesses exemplos por um valor de **Release** da [tabela de versões do .NET Framework](#version_table).

## <a name="find-older-net-framework-versions-182114"></a>Encontrar versões mais antigas do .NET Framework (1&#8211;4)

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a>Encontrar as versões 1&#8211;4 do .NET Framework no Registro 
  
1. No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.
  
    Você precisará ter credenciais administrativas para executar o REGEDIT.  

2. No Editor do Registro, abrir a seguinte subchave: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:  

    - Para as versões 1.1 a 3.5 do .NET Framework, cada versão instalada é listada como uma subchave na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**. Por exemplo, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. O número de versão é armazenado como um valor na entrada **Version** da subchave da versão. 
     
    - Para o .NET Framework 4, a entrada **Version** está localizada na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client**, na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** ou em ambas as subchaves.

    > [!NOTE]
    > A pasta **NET Framework Setup** no Registro não começa com um ponto.

    A figura a seguir mostra a subchave e sua entrada **Version** para o .NET Framework 3.5.

    ![A entrada do Registro para o .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 e versões anteriores")

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a>Encontrar as versões 1&#8211;4 do .NET Framework com o código

- Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** no Registro do Windows.

O seguinte exemplo localiza as versões 1&#8211;4 do .NET Framework que estão instaladas:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a>Encontrar versões do CLR
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a>Localizar a versão atual do CLR com Clrver.exe

Use a [ferramenta de Versão do CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) para determinar quais versões do CLR estão instaladas em um computador:

- Em um [Prompt de Comando do Desenvolvedor para o Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), insira `clrver`.

    Saída de exemplo:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a>Localizar a versão atual do CLR com a classe Environment

> [!IMPORTANT]
> Para o .NET Framework 4.5 e versões posteriores, não use a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do CLR. Em vez disso, consulte o Registro, conforme descrito em [Encontrar versões 4.5 e posteriores do .NET Framework com o código](#net_d).

1. Consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version>. 

    O objeto `System.Version` retornado identifica a versão do tempo de execução que está executando o código. Ele não retorna versões de assembly nem outras versões do tempo de execução que possam ter sido instaladas no computador.

    Para as versões 4, 4.5, 4.5.1 e 4.5.2 do .NET Framework, a representação de cadeia de caracteres do objeto <xref:System.Version> retornado tem o formato 4.0.30319.*xxxxx*. Para o .NET Framework 4.6 e versões posteriores, ele tem o formato 4.0.30319.42000.    

2. Depois de ter o objeto `Version`, consulte-o da seguinte maneira:

   - Para o identificador de versão principal (por exemplo, *4* para a versão 4.0), use a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType>.

   - Para o identificador de versão secundária (por exemplo, *0* para a versão 4.0), use a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

   - Para a cadeia de caracteres de versão inteira (por exemplo, *4.0.30319.18010*), use o método <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Esse método retorna um único valor que reflete a versão do tempo de execução que está executando o código. Ele não retorna versões de assembly nem outras versões do tempo de execução que possam ter sido instaladas no computador.



O seguinte exemplo usa a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do CLR:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Consulte também

- [Como: Determinar quais atualizações do .NET Framework estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalar o .NET Framework para desenvolvedores](../install/guide-for-developers.md)
- [Versões e dependências do .NET Framework](versions-and-dependencies.md)
