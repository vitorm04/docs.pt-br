---
title: "Como determinar quais versões do .NET Framework estão instaladas | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
caps.latest.revision: 62
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f2aca8f5f977d278fd326dfb20267d9bf1a8262
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Como determinar quais versões do .NET Framework estão instaladas
Você pode instalar e executar várias versões do .NET Framework em seus computadores. Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário. Observe que o .NET Framework consiste em dois componentes, que são versões separadas:  
  
-   Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos. O .NET Framework e assemblies que compartilham o mesmo número de versão.  
  
-   O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos. O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Para obter uma lista precisa nas versões do .NET Framework instaladas no computador, você pode ver o Registro ou consultar o Registro em código:  
  
 [Visualizar o Registro (versões 1 a 4)](#net_a)  
 [Visualizar o Registro (versões 4.5 e posteriores)](#net_b)  
 [Usar o código para consultar o Registro (versões 1 a 4)](#net_c)  
 [Usar o código para consultar o Registro (versões 4.5 e posteriores)](#net_d)  
  
 Para encontrar a versão CLR, é possível usar uma ferramenta ou código:  
  
 [Usar a ferramenta Clrver](#clr_a)  
 [Usar o código para consultar a classe System.Environment](#clr_b)  
  
 Para saber mais sobre como detectar as atualizações instaladas para cada versão do .NET Framework, veja [Como determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Para saber mais sobre como instalar o .NET Framework, veja o [Guia de instalação](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>Para encontrar versões do .NET Framework visualizando o Registro (.NET Framework 1 a 4)  
  
1.  No menu **Iniciar**, escolha **Executar**.  
  
2.  Na caixa **Abrir**, insira **regedit.exe**.  
  
     Você deve ter credenciais administrativas para executar o regedit.exe.  
  
3.  No Editor do Registro, abrir a seguinte subchave:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     As versões instaladas estão listadas abaixo da subchave NDP. O número de versão é armazenado na entrada **Version**. Para o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a entrada **Version** está sob a subchave Client ou Full (em NDP) ou em ambas as subchaves.  
  
    > [!NOTE]
    >  A pasta "NET Framework Setup” no Registro não começa por um ponto.  
  
<a name="net_b"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>Para encontrar versões do .NET Framework visualizando o Registro (.NET Framework 4.5 e posteriores)  
  
1.  No menu **Iniciar**, escolha **Executar**.  
  
2.  Na caixa **Abrir**, insira **regedit.exe**.  
  
     Você deve ter credenciais administrativas para executar o regedit.exe.  
  
3.  No Editor do Registro, abrir a seguinte subchave:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`  
  
     Observe que o caminho até a subchave `Full` inclui a subchave `Net Framework` em vez de `.NET Framework`.  
  
    > [!NOTE]
    >  Se a subchave `Full` não estiver presente, então você não terá o .NET Framework 4.5 ou posterior instalado.  
  
     Procure um valor DWORD chamado `Release`. A existência da DWORD `Release` indica que o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou mais recente foi instalado naquele computador.  
  
     ![A entrada do Registro para o .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")  
  
     O valor do DWORD de `Release` indica qual versão do .NET Framework está instalada.  
  
    |Valor da liberação de DWORD|Versão|  
    |--------------------------------|-------------|  
    |378389|.NET Framework 4.5|  
    |378675|.NET Framework 4.5.1 instalado com Windows 8.1 ou Windows Server 2012 R2|  
    |378758|.NET Framework 4.5.1 instalado no Windows 8, Windows 7 SP1 ou Windows Vista SP2|  
    |379893|.NET Framework 4.5.2|  
    |Em sistemas Windows 10: 393295<br /><br /> Em todas as outras versões do sistema operacional: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|  
    |Em sistemas com a Atualização de novembro do Windows 10: 394254<br /><br /> Em todas as outras versões do sistema operacional: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|  
    |Na Atualização de Aniversário do Windows 10: 394802<br /><br /> Em todas as outras versões do sistema operacional: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |No Windows 10 Creators Update: 460798 | .NET Framework 4.7 |  
  
<a name="net_c"></a>   
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>Para encontrar versões do .NET Framework consultando o Registro em código (.NET Framework 1 a 4)  
  
-   Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> para acessar a subchave Software\Microsoft\NET Framework Setup\NDP\ em HKEY_LOCAL_MACHINE no Registro do Windows.  
  
     O código a seguir mostra um exemplo dessa consulta.  
  
    > [!NOTE]
    >  Este código não mostra como detectar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou posterior. Verifique a DWORD `Release` para detectar as versões, conforme descrito na seção anterior. Para saber o código que detecta o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou versões posteriores, veja a próxima seção deste artigo.  
  
     [!code-csharp[ListVersions#0](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#0)]
     [!code-vb[ListVersions#0](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#0)]  
    [!code-csharp[ListVersions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#1)]
    [!code-vb[ListVersions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#1)]  
  
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
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>Para encontrar versões do .NET Framework consultando o Registro em código (.NET Framework 4.5 e posteriores)  
  
1.  A existência de DWORD `Release` indica que o .NET Framework 4.5 ou posteriores foi instalado no computador. O valor da palavra-chave indica a versão instalada. Para verificar essa palavra-chave, use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> da classe <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> para acessar a subchave Software\Microsoft\NET Framework Setup\NDP\v4\Full em HKEY_LOCAL_MACHINE no Registro do Windows.  
  
2.  Verifique o valor da palavra-chave `Release` para determinar a versão instalada. Para ser compatível direto, você pode verificar se há um valor maior ou igual aos valores listados na tabela. Veja a seguir as versões e palavras-chave `Release` associadas do .NET Framework.  
  
    |Versão|Valor da liberação de DWORD|  
    |-------------|--------------------------------|  
    |.NET Framework 4.5|378389|  
    |.NET Framework 4.5.1 instalado com Windows 8.1|378675|  
    |.NET Framework 4.5.1 instalado no Windows 8, Windows 7 SP1 ou Windows Vista SP2|378758|  
    |.NET Framework 4.5.2|379893|  
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] instalado com o Windows 10|393295|  
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] instalado em todas as outras versões do sistema operacional Windows|393297|  
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] instalado no Windows 10|394254|  
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] instalado em todas as outras versões do sistema operacional Windows|394271|  
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] instalado na Atualização de Aniversário do Windows 10|394802|  
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] instalado em todas as outras versões do sistema operacional Windows|394806|
    |.NET Framework 4.7 instalado no Windows 10 Creators Update|460798|  
  
     A exemplo a seguir verifica o valor `Release` no Registro para determinar se o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou uma versão posterior do .NET Framework está instalada.  
  
     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/Versions45Plus.cs#5)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/Versions45Plus.vb#5)]  
  
     Este exemplo segue a prática recomendada para a verificação de versão:  
  
    -   Ele verifica se o valor da entrada `Release` é *maior ou igual* ao valor das chaves de versão conhecidas.  
  
    -   Ele verifica na ordem da versão mais recente para a versão mais antiga.  
  
<a name="clr_a"></a>   
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Para localizar a versão de tempo de execução atual usando a ferramenta Clrver  
  
-   Use a Ferramenta de Versão do CLR (Clrver.exe) para determinar quais versões do Common Language Runtime estão instaladas em um computador.  
  
     Em um prompt de comando do Visual Studio, insira `clrver`. Esse comando gera uma saída semelhante à seguinte:  
  
    ```  
    Versions installed on the machine:  
    v2.0.50727  
    v4.0.30319  
    ```  
  
     Para saber mais sobre como usar essa ferramenta, veja [ Clrver.exe (Ferramenta de Versão do CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).  
  
<a name="clr_b"></a>   
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Localizar a versão do tempo de execução atual ao consultar a classe Environment no código  
  
-   Confira a propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> para recuperar um objeto <xref:System.Version> que identifica a versão do tempo de execução que está executando o código. Você pode usar a propriedade <xref:System.Version.Major%2A?displayProperty=fullName> para obter o identificador de versão principal (por exemplo, "4" para a versão 4.0), a propriedade <xref:System.Version.Minor%2A?displayProperty=fullName> para obter o identificador de versão secundária (por exemplo, "0" para a versão 4.0), ou o método <xref:System.Object.ToString%2A?displayProperty=fullName> para obter a cadeia de caracteres de versão inteira (por exemplo, "4.0.30319.18010", conforme mostra o código a seguir). Essa propriedade retorna um valor único que reflete a versão do tempo de execução que está executando o código; ela não retorna versões do assembly ou outras versões de tempo de execução que podem ter sido instaladas no computador.  
  
     Para as versões do .NET Framework 4, 4.5, 4.5.1 e 4.5.2, a propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> retorna um objeto <xref:System.Version> cuja representação de cadeia de caracteres tem a forma `4.0.30319.xxxxx`. Para o .NET Framework 4.6 e posterior, ela tem a forma `4.0.30319.42000`.  
  
    > [!IMPORTANT]
    >  Para o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e posterior, não recomendamos o uso da propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> para detectar a versão do tempo de execução. Em vez disso, recomendamos a consulta do Registro, conforme descrito na seção [Para encontrar versões do .NET Framework consultando o Registro no código (.NET Framework 4.5 e posterior)](#net_d) neste artigo.  
  
     Confira um exemplo de consulta da propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> para obter informações de versão de tempo de execução:  
  
     [!code-csharp[ListVersions#0](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#0)]
     [!code-vb[ListVersions#0](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#0)]  
    [!code-csharp[ListVersions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#2)]
    [!code-vb[ListVersions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#2)]  
  
     O exemplo produz uma saída semelhante à seguinte:  
  
    ```  
    Version: 4.0.30319.18010  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Como determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)   
 [Guia de instalação](../../../docs/framework/install/guide-for-developers.md)   
 [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)
