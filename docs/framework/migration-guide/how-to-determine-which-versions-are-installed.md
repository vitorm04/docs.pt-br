---
title: Determinar quais versões do .NET Framework estão instaladas
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738194"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Como determinar quais versões do .NET Framework estão instaladas

Os usuários podem [instalar](../install/index.md) e executar várias versões do .NET Framework em seus computadores. Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário.

O .NET Framework consiste em dois componentes principais, que têm o controle de versão feito separadamente:

- Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos. O .NET Framework e assemblies que compartilham o mesmo número de versão.

- O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos. O CLR é identificado por seu próprio número de versão (consulte [versões e dependências](versions-and-dependencies.md)).

> [!NOTE]
> Cada nova versão do .NET Framework retém recursos de versões anteriores e adiciona novos recursos. Você pode carregar várias versões do .NET Framework em um único computador ao mesmo tempo, o que significa que você pode instalar o .NET Framework sem precisar desinstalar as versões anteriores. Em geral, você não deve desinstalar as versões anteriores do .NET Framework, porque um aplicativo que você usa pode depender de uma versão específica e pode ser interrompido caso essa versão seja removida.
>
> Há uma diferença entre a versão do .NET Framework e a versão do CLR:
>
> - A versão do .NET Framework baseia-se no conjunto de assemblies que forma a biblioteca de classes .NET Framework. Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2.
> - A versão do CLR baseia-se no runtime no qual os aplicativos .NET Framework são executados. Uma única versão do CLR geralmente dá suporte a várias versões do .NET Framework. Por exemplo, o CLR versão 4.0.30319.*xxxxx* dá suporte ao .NET Framework versões 4 a 4.5.2, em que *xxxxx* é menor que 42000; o CLR versão 4.0.30319.42000 dá suporte a versões do .NET Framework a partir do .NET Framework 4.6.
>
> Para obter mais informações sobre as versões, confira [Versões e dependências do .NET Framework](versions-and-dependencies.md).

O registro contém uma lista das versões de .NET Framework instaladas em um computador. Você pode usar o editor do registro para exibir o registro ou consultá-lo com código:

- Encontre versões mais recentes do .NET Framework (4.5 e posterior):

  - [Usar o Editor do Registro para encontrar versões do .NET Framework](#net_b)
  - [Usar o código para consultar versões do .NET Framework no Registro](#net_d)
  - [Usar o PowerShell para consultar versões do .NET Framework no Registro](#ps_a)

- Localizar versões mais antigas do .NET Framework (de 1 a 4):

  - [Usar o Editor do Registro para encontrar versões do .NET Framework](#net_a)
  - [Usar o código para consultar versões do .NET Framework no Registro](#net_c)

Para obter uma lista das versões do CLR instaladas em um computador, use uma ferramenta ou o código:

- [Usar a ferramenta Clrver](#clr_a)
- [Usar o código para consultar a classe Environment](#clr_b)

Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, consulte [como: determinar quais .NET Framework atualizações estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>Encontrar versões mais recentes do .NET Framework (4.5 e posterior)

Você pode usar o editor do registro para localizar informações de versão no registro ou pode consultar o registro programaticamente.

<a name="net_b"></a>

### <a name="use-registry-editor"></a>Usar o editor do registro

1. No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.

     Você precisará ter credenciais administrativas para executar o REGEDIT.

2. No editor do registro, abra a seguinte subchave: **HKEY_LOCAL_MACHINE \Software\microsoft\net Framework Setup\NDP\v4\Full**. Se a subchave **Full** não estiver presente, você não terá o .NET Framework 4.5 ou posterior instalado.

    > [!NOTE]
    > A pasta **NET Framework Setup** no Registro *não* começa com um ponto.

3. Verifique se há uma entrada DWORD chamada **Release**. Se ele existir, você terá .NET Framework 4,5 ou posterior instalado. Seu valor é uma chave de versão que corresponde a uma versão específica do .NET Framework. Na figura a seguir, por exemplo, o valor da entrada de **versão** é 378389, que é a chave de versão para .NET Framework 4,5.

   ![Entrada de registro para o .NET Framework 4,5](./media/clr-installdir.png "Entrada de registro para o .NET Framework 4,5")

A tabela a seguir lista o valor de **Release** DWORD em cada sistema operacional individual para o .NET Framework 4.5 e versões posteriores.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Versão do .NET Framework|Valor da liberação de DWORD|
|--------------------------------|-------------|
|.NET Framework 4,5|Todos os sistemas operacionais Windows: 378389|
|.NET Framework 4.5.1|No Windows 8.1 e no Windows Server 2012 R2:378675<br />Em todos os outros sistemas operacionais Windows: 378758|
|.NET Framework 4.5.2|Todos os sistemas operacionais Windows: 379893|
|.NET Framework 4.6|No Windows 10:393295<br />Em todos os outros sistemas operacionais Windows: 393297|
|.NET Framework 4.6.1|Em sistemas com a Atualização de novembro do Windows 10: 394254<br />Em todos os outros sistemas operacionais Windows (incluindo o Windows 10): 394271|
|.NET Framework 4.6.2|Na Atualização de Aniversário do Windows 10 e Windows Server 2016: 394802<br />Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 394806|
|.NET Framework 4.7|No Windows 10 Creators Update: 460798<br />Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 460805|
|.NET Framework 4.7.1|Na atualização dos criadores de outono do Windows 10 e do Windows Server, versão 1709:461308<br/>Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 461310|
|.NET Framework 4.7.2|Na atualização do Windows 10 de abril de 2018 e Windows Server, versão 1803:461808<br/>Em todos os sistemas operacionais Windows, exceto Windows 10 de abril de 2018 atualização e Windows Server, versão 1803:461814|
|.NET Framework 4.8|No Windows 10 maio 2019 atualização e Windows 10 de novembro de 2019 atualização: 528040<br/>Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 528049|

#### <a name="specific-version"></a>Versão específica

Para determinar se uma versão *específica* do .NET Framework está instalada em uma versão específica do sistema operacional Windows, teste se o valor DWORD da **versão** é *igual ao* valor listado na tabela. Por exemplo, para determinar se o .NET Framework 4.6 está presente em um sistema Windows 10, teste o valor de **Release** que é *igual a* 393295.

#### <a name="minimum-version"></a>Versão mínima

Para determinar se uma versão *mínima* do .NET Framework está presente, use o menor valor DWORD da **versão** para essa versão da tabela anterior. (Para sua conveniência, os valores mínimos também são listados na tabela a seguir.)

Por exemplo, se seu aplicativo for executado em .NET Framework 4,8 ou em uma versão posterior, teste um valor DWORD de versão *maior ou igual a* 528040.

|Versão do .NET Framework|Valor mínimo da versão DWORD|
|--------------------------------|-------------|
|.NET Framework 4,5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|
|.NET Framework 4.8|528040|

#### <a name="multiple-versions"></a>Várias versões

Para testar várias versões, comece testando um valor que seja *maior ou igual ao* menor valor de DWORD da versão mais recente do .NET Framework e compare o valor com o menor valor de DWORD para cada versão anterior. Por exemplo, se seu aplicativo exigir o .NET Framework 4.7 ou posterior e você quiser determinar a versão específica atual do .NET Framework, comece testando um valor de **RELEASE** DWORD que seja *maior ou igual a* 461808 (o menor valor de DWORD para o .NET Framework 4.7.2). Em seguida, compare o valor de **RELEASE** DWORD com o menor valor para cada versão posterior do .NET Framework.

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a>Consultar o registro usando código

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

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a>Usar o PowerShell para verificar se há uma versão mínima exigida

Use comandos do PowerShell para verificar o valor da entrada **Release** da subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.

Os exemplos a seguir verificam o valor da entrada **Release** para determinar se o .NET Framework 4.6.2 ou posterior está instalado. Esse código retornará `True` se ele estiver instalado; caso contrário, retornará `False`.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Para verificar se há uma versão de .NET Framework mínima necessária diferente, substitua `394802` no exemplo por um valor da [tabela de versão .NET Framework](#version_table). Use o menor valor mostrado para essa versão.

## <a name="find-older-net-framework-versions-1-through-4"></a>Localizar versões mais antigas do .NET Framework (1 a 4)

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a>Usar o editor do registro (versões mais antigas do Framework)

1. No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.

    Você precisará ter credenciais administrativas para executar o REGEDIT.

2. No editor do registro, abra a seguinte subchave: **HKEY_LOCAL_MACHINE \Software\microsoft\net Framework Setup\NDP**:

    - Para as versões 1.1 a 3.5 do .NET Framework, cada versão instalada é listada como uma subchave na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**. Por exemplo, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. O número de versão é armazenado como um valor na entrada **Version** da subchave da versão.

    - Para o .NET Framework 4, a entrada **Version** está localizada na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client**, na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** ou em ambas as subchaves.

    > [!NOTE]
    > A pasta **NET Framework Setup** no Registro não começa com um ponto.

    A figura a seguir mostra a subchave e sua entrada **Version** para o .NET Framework 3.5.

    ![A entrada do registro para o .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 e versões anteriores")

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a>Consultar o registro usando código (versões mais antigas do Framework)

Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** no Registro do Windows.

O exemplo a seguir localiza as .NET Framework de 1 a 4 versões instaladas:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Encontrar versões do CLR

<a name="clr_a"></a>

### <a name="use-clrverexe"></a>Usar CLRVer. exe

Use a [ferramenta de Versão do CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) para determinar quais versões do CLR estão instaladas em um computador:

- Em um [Prompt de Comando do Desenvolvedor para o Visual Studio](../tools/developer-command-prompt-for-vs.md), insira `clrver`.

    Saída de exemplo:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a>Usar a classe de ambiente

> [!IMPORTANT]
> Para o .NET Framework 4.5 e versões posteriores, não use a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do CLR. Em vez disso, consulte o Registro, conforme descrito em [Encontrar versões 4.5 e posteriores do .NET Framework com o código](#net_d).

1. Consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version>.

    O objeto `System.Version` retornado identifica a versão do runtime que está executando o código. Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.

    Nas versões 4, 4.5, 4.5.1 e 4.5.2 do .NET Framework, a representação de cadeia de caracteres do objeto <xref:System.Version> retornado tem o formato 4.0.30319.*xxxxx*, em que *xxxxx* é menor que 42000. Para o .NET Framework 4.6 e versões posteriores, ele tem o formato 4.0.30319.42000.

2. Depois de ter o objeto `Version`, consulte-o da seguinte maneira:

   - Para o identificador de versão principal (por exemplo, *4* para a versão 4.0), use a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType>.

   - Para o identificador de versão secundária (por exemplo, *0* para a versão 4.0), use a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

   - Para a cadeia de caracteres de versão inteira (por exemplo, *4.0.30319.18010*), use o método <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Esse método retorna um único valor que reflete a versão do runtime que está executando o código. Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.

O seguinte exemplo usa a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do CLR:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Consulte também

- [Como determinar quais .NET Framework atualizações estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalar o .NET Framework para desenvolvedores](../install/guide-for-developers.md)
- [Versões e dependências do .NET Framework](versions-and-dependencies.md)
