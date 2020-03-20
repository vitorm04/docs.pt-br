---
title: Determinar quais versões do .NET Framework estão instaladas
description: Use código, regedit.exe ou PowerShell para detectar quais versões do .NET Framework são instaladas em uma máquina consultando o registro do Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093819"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Como determinar quais versões do .NET Framework estão instaladas

Os usuários podem [instalar](../install/index.md) e executar várias versões do .NET Framework em seus computadores. Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário. O registro contém uma lista das versões .NET Framework instaladas em um computador.

O .NET Framework consiste em dois componentes principais, que têm o controle de versão feito separadamente:

- Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos. O .NET Framework e assemblies que compartilham o mesmo número de versão. Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2.

- O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos. Uma única versão do CLR geralmente dá suporte a várias versões do .NET Framework. Por exemplo, versão CLR 4.0.30319. *xxxxx* onde *xxxxx* é menor que 42000, suporta versões .NET Framework 4 a 4.5.2. A versão CLR maior ou igual a 4.0.30319.42000 suporta versões .NET Framework a partir de .NET Framework 4.6.

As ferramentas mantidas pela comunidade estão disponíveis para ajudar a detectar quais versões do .NET Framework estão instaladas:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Uma ferramenta de linha de comando .NET 2.0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Um módulo PowerShell 2.0.

Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, consulte [Como: Determinar quais atualizações do .NET Framework estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Detectar .NET Framework 4.5 e versões posteriores

A versão do .NET Framework (4.5 e posterior) instalada em uma máquina está listada no registro em **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Se a subchave **Completa** estiver faltando, o .NET Framework 4.5 ou superior não estiver instalado.

> [!NOTE]
> A sub-chave **NET Framework Setup** no caminho do registro *não* começa com um período.

O valor de REG_DWORD de **liberação** no registro representa a versão do .NET Framework instalado.

<a name="version_table"></a>

| Versão do .NET Framework | Valor da **Liberação** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Todos os sistemas operacionais Windows: 378389 |
| .NET Framework 4.5.1   | No Windows 8.1 e Windows Server 2012 R2: 378675<br />Em todos os outros sistemas operacionais Windows: 378758 |
| .NET Framework 4.5.2   | Todos os sistemas operacionais Windows: 379893 |
| .NET framework 4.6     | No Windows 10: 393295<br />Em todos os outros sistemas operacionais Windows: 393297 |
| .NET Framework 4.6.1   | Em sistemas com a Atualização de novembro do Windows 10: 394254<br />Em todos os outros sistemas operacionais Windows (incluindo windows 10): 394271 |
| .NET Framework 4.6.2   | Na Atualização de Aniversário do Windows 10 e Windows Server 2016: 394802<br />Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 394806 |
| .NET Framework 4.7     | No Windows 10 Creators Update: 460798<br />Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 460805 |
| .NET Framework 4.7.1   | No Windows 10 Fall Creators Update e Windows Server, versão 1709: 461308<br/>Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 461310 |
| .NET Framework 4.7.2   | No Windows 10 Abril 2018 Update e Windows Server, versão 1803: 461808<br/>Em todos os sistemas operacionais Windows que não o Windows 10 abril 2018 Update e Windows Server, versão 1803: 461814 |
| .NET Framework 4.8     | No Windows 10 May 2019 Update e Windows 10 November 2019 Atualização: 528040<br/>No Windows 10 e Windows Server, versão 1909: 528209<br/>Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 528049 |

### <a name="minimum-version"></a>Versão mínima

Para determinar se existe uma versão *mínima* do Quadro .NET, use o menor valor **de REG_DWORD de versão** para essa versão da tabela anterior.

Por exemplo, se o aplicativo for executado em .NET Framework 4.8 ou uma versão posterior, teste para uma **versão** REG_DWORD valor maior *ou igual a* 528040.

| Versão do .NET Framework | Valor mínimo |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
| .NET Framework 4.7.2   | 461808 |
| .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Use o Editor de Registro

01. No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.

    Você precisará ter credenciais administrativas para executar o REGEDIT.

01. No Editor de Registro, abra a seguinte subchave: **HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Microsoft NET Framework Setup\\NDP\\v4\\Full**. Se a subchave **Full** não estiver presente, você não terá o .NET Framework 4.5 ou posterior instalado.

01. Verifique se há uma entrada REG_DWORD chamada **Release**. Se ele existir, então você tem .NET Framework 4.5 ou posteriorinstalado. Seu valor corresponde a uma versão específica do Quadro .NET. Na figura a seguir, por exemplo, o valor da entrada **de lançamento** é 528040, que é a chave de liberação para .NET Framework 4.8.

    ![Entrada de registro para o Quadro .NET 4.5](./media/clr-installdir.png "Entrada de registro para o Quadro .NET 4.5")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Use o PowerShell para verificar se há uma versão mínima

Use os comandos PowerShell para verificar o valor da entrada de **lançamento** do **software HKEY_LOCAL_MACHINE\\software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.

Os exemplos a seguir verificam o valor da entrada **Release** para determinar se o .NET Framework 4.6.2 ou posterior está instalado. Esse código retornará `True` se ele estiver instalado; caso contrário, retornará `False`.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Consultar o registro usando código

01. Use <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> os <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> métodos e métodos para acessar o **software\\HKEY_LOCAL_MACHINE Microsoft\\\\NET Framework Setup\\NDP\\v4\\Subchave completa** no registro do Windows.

    > [!IMPORTANT]
    > Se o aplicativo que você está executando for de 32 bits e estiver em execução no Windows de 64 bits, os caminhos de registro serão diferentes dos listados anteriormente. O registro de 64 bits está disponível na **subchave HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node.\\ ** Por exemplo, a subchave de registro para .NET Framework 4.5 é **\\HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Wow6432Node\\Microsoft\\NET Framework Setup NDP v4\\Full**.

01. Verifique o **valor de versão** REG_DWORD para determinar a versão instalada. Para compatibilidade com a versão atual, verifique se há um valor superior ou igual ao valor listado na [tabela de versões do .NET Framework](#version_table).

O seguinte exemplo verifica o valor da entrada **Release** no Registro para encontrar o .NET Framework 4.5 e versões posteriores que estão instaladas:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Este exemplo segue a prática recomendada para a verificação de versão:

- Ele verifica se o valor da entrada **Release** é *superior ou igual* ao valor das chaves de versão conhecidas.
- Ele verifica na ordem da versão mais recente para a versão mais antiga.

## <a name="detect-net-framework-10-through-40"></a>Detectar .NET Framework 1.0 a 4.0

Cada versão do .NET Framework de 1.1 a 4.0 é listada como uma subchave no **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**. A tabela a seguir lista o caminho para cada versão do .NET Framework. Para a maioria das versões, `1` há um valor **de Instalação** REG_DWORD para indicar que esta versão está instalada. Nessas subchaves, há também uma **versão** REG_SZ valor que contém uma seqüência de versões.

> [!NOTE]
> A sub-chave **NET Framework Setup** no caminho do registro *não* começa com um período.

| Versão-framework  | Subchave de registro | Valor |
| ------------------ | --------------- | ----- |
| 1.0                | **Software HKLM\\\\Microsoft\\. Política\\\\NETFramework v1.0\\3705**     | **Instalar** REG_SZ é igual`1` |
| 1,1                | **HKLM\\\\Software\\Microsoft NET\\\\Framework Setup NDP v1.1.4322**   | **Instalar** REG_DWORD é igual.`1` |
| 2,0                | **HKLM\\\\Software\\Microsoft NET\\\\Framework Setup NDP v2.0.50727**  | **Instalar** REG_DWORD é igual.`1` |
| 3.0                | **Configuração\\do\\\\HKLM\\Software\\Microsoft NET\\Framework NDP v3.0** | **InstallSuccess** REG_DWORD é igual.`1` |
| 3,5                | **HKLM\\\\Software\\Microsoft NET\\\\Framework Setup NDP v3.5**        | **Instalar** REG_DWORD é igual.`1` |
| Perfil do Cliente 4.0 | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**  | **Instalar** REG_DWORD é igual.`1` |
| 4.0 Perfil Completo   | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**    | **Instalar** REG_DWORD é igual.`1` |

> [!IMPORTANT]
> Se o aplicativo que você está executando for de 32 bits e estiver em execução no Windows de 64 bits, os caminhos de registro serão diferentes dos listados anteriormente. O registro de 64 bits está disponível na **subchave HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node.\\ ** Por exemplo, a subchave de registro para .NET Framework 3.5 é **\\HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Wow6432Node\\\\Microsoft NET Framework Setup NDP v3.5**.

Observe que o caminho de registro para a subchave .NET Framework 1.0 é diferente dos outros.

### <a name="use-registry-editor-older-framework-versions"></a>Use o Editor de Registro (versões de framework mais antigas)

01. No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.

    Você precisará ter credenciais administrativas para executar o REGEDIT.

01. Abra a subchave que corresponde à versão que você deseja verificar. Use a tabela na seção [Detectar .NET Framework 1.0 a 4.0.](#detect-net-framework-10-through-40)

    A figura a seguir mostra a sub-chave e seu valor **de versão** para .NET Framework 3.5.

    ![A entrada de registro para o Quadro .NET 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 e versões anteriores")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Consulte o registro usando código (versões de framework mais antigas)

Use <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> a classe para acessar a **subchave de\\\\configuração do\\\\microsoft net framework do HKEY_LOCAL_MACHINE** no registro do Windows.

> [!IMPORTANT]
> Se o aplicativo que você está executando for de 32 bits e estiver em execução no Windows de 64 bits, os caminhos de registro serão diferentes dos listados anteriormente. O registro de 64 bits está disponível na **subchave HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node.\\ ** Por exemplo, a subchave de registro para .NET Framework 3.5 é **\\HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Wow6432Node\\\\Microsoft NET Framework Setup NDP v3.5**.

O exemplo a seguir encontra as versões .NET Framework 1 a 4 instaladas:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Encontrar versões do CLR

O .NET Framework CLR instalado com o .NET Framework é versão separada. Existem duas maneiras de detectar a versão do .NET Framework CLR:

- **A ferramenta Clrver.exe**

  Use a [ferramenta ClR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) para determinar quais versões do CLR estão instaladas em um computador. Abra o [Prompt de Comando do Desenvolvedor para o Visual Studio](../tools/developer-command-prompt-for-vs.md) e insira `clrver`.

  Saída de exemplo:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **A `Environment` classe**

  > [!IMPORTANT]
  > Para versões .NET Framework 4.5 e <xref:System.Environment.Version%2A?displayProperty=nameWithType> posteriores, não use a propriedade para detectar a versão do CLR. Em vez disso, consultar o registro conforme descrito em [Detect .NET Framework 4.5 e versões posteriores](#detect-net-framework-45-and-later-versions).
  
  01. Consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version>.
  
      O objeto `System.Version` retornado identifica a versão do runtime que está executando o código. Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.
  
      Para as versões 4, 4.5, 4.5.1 e 4.5.2 do <xref:System.Version> .NET Framework, a representação de seqüência do objeto retornado tem o formulário 4.0.30319. *xxxxx*, onde *xxxxx* é menor que 42000. Para as versões .NET Framework 4.6 e posteriores, ele tem o formulário 4.0.30319.42000.
  
  01. Depois de ter o objeto **Versão,** consulte-o da seguinte forma:
  
      - Para o identificador de versão principal (por exemplo, *4* para a versão 4.0), use a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType>.
  
      - Para o identificador de versão secundária (por exemplo, *0* para a versão 4.0), use a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType>.
  
      - Para a cadeia de caracteres de versão inteira (por exemplo, *4.0.30319.18010*), use o método <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Esse método retorna um único valor que reflete a versão do runtime que está executando o código. Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.

  O seguinte exemplo usa a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do CLR:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Confira também

- [Como: Determinar quais atualizações do Framework .NET estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalar o .NET Framework para desenvolvedores](../install/guide-for-developers.md)
- [Versões e dependências do .NET Framework](versions-and-dependencies.md)
