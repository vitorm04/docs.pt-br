---
title: 'Como: Determinar quais versões do .NET Framework estão instaladas'
ms.date: 04/10/2018
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
ms.openlocfilehash: 890ce1e9a23d57121cd714252444e5ff1caa6b19
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396871"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Como: Determinar quais versões do .NET Framework estão instaladas

Você pode instalar e executar várias versões do .NET Framework em seus computadores. Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário. Observe que o .NET Framework consiste em dois componentes, que são versões separadas:  
  
-   Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos. O .NET Framework e assemblies que compartilham o mesmo número de versão.  
  
-   O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos. O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Para obter uma lista precisa nas versões do .NET Framework instaladas no computador, você pode ver o Registro ou consultar o Registro em código:  
  
 [Visualizar o Registro (versões 1 a 4)](#net_a)  
 [Visualizar o Registro (versões 4.5 e posteriores)](#net_b)  
 [Usar o código para consultar o Registro (versões 1 a 4)](#net_c)  
 [Usar o código para consultar o Registro (versões 4.5 e posteriores)](#net_d)  
 [Uso do PowerShell para consultar o Registro (versões 4.5 e posteriores)](#ps_a)  
  
 Para encontrar a versão CLR, é possível usar uma ferramenta ou código:  
  
 [Usar a ferramenta Clrver](#clr_a)  
 [Usar o código para consultar a classe System.Environment](#clr_b)  
  
 Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, confira [Como: Determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Para obter mais informações sobre como instalar o .NET Framework, consulte [Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>Para encontrar versões do .NET Framework visualizando o Registro (.NET Framework 1 a 4)  
  
1.  No menu **Iniciar**, escolha **Executar**.  
  
2.  Na caixa **Abrir**, insira **regedit.exe**.  
  
     Você deve ter credenciais administrativas para executar o regedit.exe.  
  
3.  No Editor do Registro, abrir a seguinte subchave:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     As versões instaladas estão listadas abaixo da subchave NDP. O número de versão é armazenado na entrada **Version**. Para o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a entrada **Version** está sob a subchave Client ou Full (em NDP) ou em ambas as subchaves.  
  

    > [!NOTE]
    > A pasta "NET Framework Setup” no Registro não começa por um ponto.

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>Para encontrar versões do .NET Framework visualizando o Registro (.NET Framework 4.5 e posteriores)

1. No menu **Iniciar**, escolha **Executar**.

2. Na caixa **Abrir**, insira **regedit.exe**.

     Você deve ter credenciais administrativas para executar o regedit.exe.

3. No Editor do Registro, abrir a seguinte subchave:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Observe que o caminho até a subchave `Full` inclui a subchave `Net Framework` em vez de `.NET Framework`.

    > [!NOTE]
    > Se a subchave `Full` não estiver presente, então você não terá o .NET Framework 4.5 ou posterior instalado.

     Procure um valor DWORD chamado `Release`. A existência da DWORD `Release` indica que o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou mais recente foi instalado naquele computador.

     ![A entrada do Registro para o .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     O valor do DWORD de `Release` indica qual versão do .NET Framework está instalada.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Valor da liberação de DWORD|Versão|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|.NET Framework 4.5.1 instalado com Windows 8.1 ou Windows Server 2012 R2|
    |378758|.NET Framework 4.5.1 instalado no Windows 8, Windows 7 SP1 ou Windows Vista SP2|
    |379893|.NET Framework 4.5.2|
    |Somente em sistemas Windows 10: 393295<br /><br /> Em todas as outras versões do sistema operacional: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |Somente em sistemas com a Atualização de novembro do Windows 10: 394254<br /><br /> Em todas as outras versões do sistema operacional: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |Na Atualização de Aniversário do Windows 10 e no Windows Server 2016: 394802<br /><br /> Em todas as outras versões do sistema operacional: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |Somente na Atualização do Windows 10 para Criadores: 460798<br/><br/> Em todas as outras versões do sistema operacional: 460805 | .NET Framework 4.7 |
    |Somente no Windows 10 Fall Creators Update: 461308<br/><br/> Em todas as outras versões do sistema operacional: 461310 | .NET Framework 4.7.1 |
    |Somente na Atualização de abril de 2018 do Windows 10: 461808<br/><br/> Em todas as outras versões do sistema operacional, incluindo a Atualização de outubro de 2018 do Windows 10: 461814| .NET Framework 4.7.2 |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>Para encontrar versões do .NET Framework consultando o Registro em código (.NET Framework 1 a 4)

- Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave Software\Microsoft\NET Framework Setup\NDP\ em HKEY_LOCAL_MACHINE no registro do Windows.

     O código a seguir mostra um exemplo dessa consulta.

    > [!NOTE]
    > Este código não mostra como detectar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou posterior. Verifique a DWORD `Release` para detectar as versões, conforme descrito na seção anterior. Para saber o código que detecta o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou versões posteriores, veja a próxima seção deste artigo.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     O exemplo produz uma saída semelhante à seguinte:

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>Para encontrar versões do .NET Framework consultando o Registro em código (.NET Framework 4.5 e posteriores)

1. A existência de DWORD `Release` indica que o .NET Framework 4.5 ou posteriores foi instalado no computador. O valor da palavra-chave indica a versão instalada. Para verificar a palavra-chave, use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> da classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave Software\Microsoft\NET Framework Setup\NDP\v4\Full em HKEY_LOCAL_MACHINE no registro do Windows.

2. Verifique o valor da palavra-chave `Release` para determinar a versão instalada. Para ser compatível direto, você pode verificar se há um valor maior ou igual aos valores listados na tabela. Veja a seguir as versões e palavras-chave `Release` associadas do .NET Framework.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Versão|Valor da liberação de DWORD|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1 instalado com Windows 8.1|378675|
    |.NET Framework 4.5.1 instalado no Windows 8, Windows 7 SP1 ou Windows Vista SP2|378758|
    |.NET Framework 4.5.2|379893|
    |.NET Framework 4.6 instalado com o Windows 10|393295|
    |.NET Framework 4.6 instalado em todas as outras versões do sistema operacional Windows|393297|
    |.NET Framework 4.6.1 instalado no Windows 10|394254|
    |.NET Framework 4.6.1 instalado em todas as outras versões do sistema operacional Windows|394271|
    |.NET Framework 4.6.2 instalado na Atualização de Aniversário do Windows 10 e no Windows Server 2016|394802|
    |.NET Framework 4.6.2 instalado em todas as outras versões do sistema operacional Windows|394806|
    |.NET Framework 4.7 instalado no Windows 10 Creators Update|460798|
    |.NET Framework 4.7 instalado em todas as outras versões do sistema operacional Windows|460805|
    |.NET Framework 4.7.1 instalado no Windows 10 Falls Creators Update|461308|
    |.NET Framework 4.7.1 instalado em todas as outras versões do sistema operacional Windows|461310|
    |.NET Framework 4.7.2 instalado na Atualização de outubro de 2018 para o Windows 10|461814|
    |.NET Framework 4.7.2 instalado na Atualização de abril de 2018 do Windows 10|461808|
    |.NET Framework 4.7.2 instalado no Windows 10 Fall Creators Update e nas versões anteriores do sistema operacional|461814|
    
     A exemplo a seguir verifica o valor `Release` no Registro para determinar se o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou uma versão posterior do .NET Framework está instalada.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     Este exemplo segue a prática recomendada para a verificação de versão:

    - Ele verifica se o valor da entrada `Release` é *maior ou igual* ao valor das chaves de versão conhecidas.

    - Ele verifica na ordem da versão mais recente para a versão mais antiga.

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>Para verificar se há uma versão do .NET Framework mínima necessária consultando o Registro no PowerShell (.NET Framework 4.5 e versões posteriores)

- O exemplo a seguir verificará o valor da palavra-chave `Release` para determinar se o .NET Framework 4.6.2 ou superior estiver instalado, independentemente da versão do sistema operacional Windows (retornando `True` se ele for e `False` caso contrário).

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    É possível substituir `394802` no exemplo anterior por outro valor da tabela a seguir para verificar se há uma versão mínima necessária do .NET Framework diferente.
  
    |Versão|Valor mínimo da versão DWORD|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1|378675|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|394802|
    |.NET Framework 4.7|460798|
    |.NET Framework 4.7.1|461308|
    |.NET Framework 4.7.2|461808|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Para localizar a versão de tempo de execução atual usando a ferramenta Clrver

- Use a Ferramenta de Versão do CLR (Clrver.exe) para determinar quais versões do Common Language Runtime estão instaladas em um computador.

     Em um prompt de comando do Visual Studio, insira `clrver`. Esse comando gera uma saída semelhante à seguinte:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Para saber mais sobre como usar essa ferramenta, veja [ Clrver.exe (Ferramenta de Versão do CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Localizar a versão do tempo de execução atual ao consultar a classe Environment no código

- Consulte a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version> que identifica a versão do tempo de execução que está executando o código. Você pode usar a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType> para obter o identificador de versão principal (por exemplo, "4" para a versão 4,0), a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType> para obter o identificador de versão secundária (por exemplo, "0" para a versão 4,0), ou o método <xref:System.Object.ToString%2A?displayProperty=nameWithType> para obter a cadeia de caracteres de versão inteira (por exemplo, "4.0.30319.18010", conforme mostrado no código a seguir). Essa propriedade retorna um valor único que reflete a versão do tempo de execução que está executando o código; ela não retorna versões do assembly ou outras versões de tempo de execução que podem ter sido instaladas no computador.

     Para as versões do .NET Framework 4, 4.5, 4.5.1 e 4.5.2, a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> retorna um objeto <xref:System.Version> cuja representação da cadeia de caracteres tem a forma `4.0.30319.xxxxx`. Para o .NET Framework 4.6 e posterior, ela tem a forma `4.0.30319.42000`.

    > [!IMPORTANT]
    > Para o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e posterior, não é recomendado o uso da propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do tempo de execução. Em vez disso, recomendamos a consulta do Registro, conforme descrito na seção [Para encontrar versões do .NET Framework consultando o Registro no código (.NET Framework 4.5 e posterior)](#net_d) neste artigo.

     Veja um exemplo de consulta da propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para obtenção de informações de versão do tempo de execução:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     O exemplo produz uma saída semelhante à seguinte:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Consulte também

[Como: Determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md)  
[Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)  
