---
title: 'Como: Determinar quais versões do .NET Framework estão instaladas'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584168"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Como: Determinar quais versões do .NET Framework estão instaladas

Você pode instalar e executar várias versões do .NET Framework em seus computadores. Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário. Observe que o .NET Framework consiste em dois componentes, que são versões separadas:  
  
- Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos. O .NET Framework e assemblies que compartilham o mesmo número de versão.  
  
- O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos. O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
Para obter uma lista precisa nas versões do .NET Framework instaladas no computador, você pode ver o Registro ou consultar o Registro em código:  
  
 [Encontrar as versões 1 a 4 do .NET Framework no Registro](#net_a)  
 [Encontrar versões 4.5 e posteriores do .NET Framework no Registro](#net_b)  
 [Usar o código para consultar o Registro (versões 1 a 4)](#net_c)  
 [Usar o código para consultar o Registro (versões 4.5 e posteriores)](#net_d)  
 [Uso do PowerShell para consultar o Registro (versões 4.5 e posteriores)](#ps_a)  

 Para encontrar a versão CLR, é possível usar uma ferramenta ou código:  
  
 [Usar a ferramenta Clrver](#clr_a)  
 [Usar o código para consultar a classe System.Environment](#clr_b)  

> [!NOTE]
> Há uma diferença entre a versão do .NET Framework e a versão de CLR (common language runtime). O .NET Framework tem controle de versão com base no conjunto de assemblies que forma a Biblioteca de Classes do .NET Framework. Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2. O CLR tem controle de versão com base no tempo de execução no qual os aplicativos .NET Framework são executados, e uma única versão do CLR geralmente oferece suporte a várias versões do .NET Framework. O CLR versão 4.30319.*xxxxx* dá suporte ao .NET Framework versões 4 a 4.5.2; o CLR versão 4.30319.42000 dá suporte a versões do .NET Framework a partir do .NET Framework 4.6. Para obter mais informações, consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType>.

 Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, confira [Como: Determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Para obter mais informações sobre como instalar o .NET Framework, consulte [Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a>Encontrar versões 1-4 do .NET Framework no Registro 
  
1.  No menu **Iniciar**, escolha **Executar**.  
  
2.  Na caixa **Abrir**, insira **regedit.exe**.  
  
     Você deve ter credenciais administrativas para executar o regedit.exe.  
  
3.  No Editor do Registro, abrir a seguinte subchave:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Para o .NET Framework versões 1.1 a 3.5, as versões instaladas são listadas como as subchaves da subchave `NDP`. O número de versão é armazenado na entrada **Version** da subchave da versão. 
     
     Para o .NET Framework 4, a entrada **Version** está sob a subchave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client`, a subchave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` ou sob as duas subchaves.

    > [!NOTE]
    > A pasta "NET Framework Setup” no Registro não começa por um ponto.

    A figura a seguir mostra a subchave para o .NET Framework 3.5, juntamente com sua entrada **Version**.

     ![A entrada do Registro para o .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 e versões anteriores")

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Encontrar versões 4.5 do .NET Framework no Registro

1. No menu **Iniciar**, escolha **Executar**.

2. Na caixa **Abrir**, insira **regedit.exe**.

     Você deve ter credenciais administrativas para executar o regedit.exe.

3. No Editor do Registro, abrir a seguinte subchave:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Observe que o caminho até a subchave `Full` inclui a subchave `Net Framework` em vez de `.NET Framework`.

    > [!NOTE]
    > Se a subchave `Full` não estiver presente, então você não terá o .NET Framework 4.5 ou posterior instalado.

     Procure um valor DWORD chamado `Release`. A existência do DWORD `Release` indica que o .NET Framework 4.5 ou posterior foi instalado no computador. Seu valor é uma chave de versão que corresponde a uma versão específica do .NET Framework. Na figura a seguir, por exemplo, o valor do DWORD `Release` é 378389, que é a chave de versão do .NET Framework 4.5. 

     ![A entrada do Registro para o .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

A tabela a seguir lista o valor mínimo do DWORD `Release` para cada versão do .NET Framework. Use esses valores da seguinte maneira:

- Para determinar se uma versão mínima do .NET Framework está presente, teste se o valor de DWORD `Release` encontrado no Registro é *maior ou igual ao* valor listado na tabela. Por exemplo, se o seu aplicativo exigir o .NET Framework 4.7 ou posterior, você verificaria a existência de um valor de versão mínima de 460798.

- Para testar várias versões, comece com a versão mais recente do .NET Framework e, em seguida, teste cada versão anterior sucessiva.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

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

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a>Encontrar versões 1-4 do .NET Framework com código

- Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave `Software\Microsoft\NET Framework Setup\NDP\` sob o branch `HKEY_LOCAL_MACHINE` no Registro do Windows.

     O código a seguir mostra um exemplo dessa consulta.

    > [!NOTE]
    > Esse código não mostra como detectar o .NET Framework 4.5 ou posterior. Verifique a DWORD `Release` para detectar as versões, conforme descrito na seção anterior. Para conhecer o código que detecta o .NET Framework 4.5 ou versões posteriores, confira a próxima seção neste artigo.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a>Encontrar versões 4.5 e posteriores do .NET Framework com código

1. A existência do DWORD `Release` na chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` indica que o .NET Framework 4.5 ou posterior foi instalado no computador. O valor da palavra-chave indica a versão instalada. Para verificar essa palavra-chave, use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> para acessar a subchave no Registro do Windows.

2. Verifique o valor da palavra-chave `Release` para determinar a versão instalada. Para ser compatível com versões posteriores, você pode verificar um valor maior ou igual ao valor listado na tabela, na seção [Encontrar versões 4.5 e posteriores do .NET Framework no Registro](#net_b).

O exemplo a seguir verifica o valor `Release` no Registro para determinar se o .NET Framework 4.5 ou uma versão posterior está instalada.

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Este exemplo segue a prática recomendada para a verificação de versão:

- Ele verifica se o valor da entrada `Release` é *maior ou igual* ao valor das chaves de versão conhecidas.

- Ele verifica na ordem da versão mais recente para a versão mais antiga.

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Verificar se há uma versão mínima necessária do .NET Framework (4.5 e posterior) com o PowerShell

O exemplo a seguir verificará o valor da palavra-chave `Release` para determinar se o .NET Framework 4.6.2 ou superior está instalado (retornando `True` se estiver, e `False`, caso contrário).

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a>Localizar a versão atual do CLR com Clrver.exe

Use a Ferramenta de Versão do CLR (Clrver.exe) para determinar quais versões do Common Language Runtime estão instaladas em um computador.

Usando um Prompt de Comando do Desenvolvedor para o Visual Studio, insira `clrver`. Esse comando gera uma saída semelhante à seguinte:

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

Para saber mais sobre como usar essa ferramenta, veja [ Clrver.exe (Ferramenta de Versão do CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a>Localizar a versão atual do CLR com a classe Environment

Recupere o valor da propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version> que identifica a versão do tempo de execução que está executando o código. Essa propriedade retorna um valor único que reflete a versão do tempo de execução que está executando o código; ela não retorna versões de assembly ou outras versões do tempo de execução que podem ter sido instaladas no computador. Você pode usar a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType> para obter o identificador de versão principal (por exemplo, "4" para a versão 4.0), a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType> para obter o identificador de versão secundária (por exemplo, "0" para a versão 4.0), ou o método <xref:System.Version.ToString%2A?displayProperty=nameWithType> para obter a cadeia de caracteres completa da versão (por exemplo, "4.0.30319.18010", conforme mostra o código a seguir). 

Para as versões do .NET Framework 4, 4.5, 4.5.1 e 4.5.2, a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> retorna um objeto <xref:System.Version> cuja representação da cadeia de caracteres tem a forma `4.0.30319.xxxxx`. Para o .NET Framework 4.6 e posterior, ela tem a forma `4.0.30319.42000`.

> [!IMPORTANT]
> Para o .NET Framework 4.5 e posterior, não é recomendado o uso da propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do tempo de execução. Em vez disso, recomendamos a consulta do Registro, conforme descrito na seção [Para encontrar versões do .NET Framework consultando o Registro no código (.NET Framework 4.5 e posterior)](#net_d) neste artigo.

O exemplo a seguir usou a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do tempo de execução:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Consulte também

- [Como: Determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md)
- [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)
