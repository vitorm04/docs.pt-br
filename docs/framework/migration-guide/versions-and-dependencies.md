---
title: .NET Framework & versões do Sistema Operacional Windows
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504052"
---
# <a name="net-framework-versions-and-dependencies"></a>Versões e dependências do .NET Framework

Cada versão do .NET Framework contém o tempo de execução do idioma comum (CLR), as bibliotecas de classe base e outras bibliotecas gerenciadas. Este artigo descreve os principais recursos do .NET Framework por versão, fornece informações sobre as versões CLR subjacentes e ambientes de desenvolvimento associados e identifica as versões que são instaladas pelo sistema operacional Windows (OS).

Cada nova versão do .NET Framework adiciona novos recursos, mas mantém recursos de versões anteriores.

O CLR é identificado pelo seu próprio número de versão. O número da versão .NET Framework é incrementado a cada versão, mas a versão CLR nem sempre é incrementada. Por exemplo, as versões .NET Framework 4, 4.5 e posteriores incluem CLR 4, mas .NET Framework 2.0, 3.0 e 3.5 incluem CLR 2.0. (Não houve versão 3 do CLR.)

> [!TIP]
>
> - Para obter uma lista completa de sistemas operacionais suportados, consulte [requisitos do sistema](../get-started/system-requirements.md).
> - Para obter informações sobre downloads, consulte [Instalar o .NET Framework para desenvolvedores](../install/guide-for-developers.md).
> - Para obter informações sobre como determinar quais versões do .NET Framework estão instaladas em um computador, consulte [Como determinar quais versões do .NET Framework estão instaladas](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informações da versão

As tabelas que seguem resumem o histórico da versão do .NET Framework e correlacionam cada versão com o Visual Studio, Windows e Windows Server. O Visual Studio suporta multi-segmentação, para que você não esteja limitado à versão do .NET Framework que está listada.

- O ícone de marca de seleção ✔️ denota versões do SISTEMA OPERACIONAL nas quais o .NET Framework está instalado, mas deve ser ativado [no Painel de Controle](../install/dotnet-35-windows-10.md) (para Windows) ou através do Server Manager (para O Windows Server).
- O ícone de sinal de ➕ denota versões do Sistema Operacional nas quais o .NET Framework não vem instalado, mas pode ser instalado.

| | |
| - | - |
| [.NET Framework 4.8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4.8

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-48)
- [Novidades em acessibilidade](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Versões do Windows**|atualização de 10 de ✔️ de maio de 2019<br/>➕ Atualização de 10 de outubro de 2018 (Versão 1809)<br/>➕ Atualização de 10 de Abril de 2018 (Versão 1803)<br/>➕ 10 Fall Creators Update (Versão 1709)<br/>➕ 10 Creators Update (Versão 1703)<br/>➕ 10 Atualização de Aniversário (Versão 1607)<br/>➕ 8.1<br/>➕|
|**Versões do Windows Server**|➕ Windows Server 2019<br/>➕ Windows Server, versão 1809<br/>➕ Windows Server, versão 1803<br/>➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br/>-528040 (atualização de maio de 2019 para o Windows 10)<br/>– 528049 (todas as outras versões de SO)<br/>(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-472)
- [Novidades em acessibilidade](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Incluída na versão do Visual Studio**|2019<sup>1</sup>|
|**Versões do Windows**|✔️ Atualização de 10 de Outubro de 2018 (Versão 1809)<br/>✔️ Atualização de 10 de Abril de 2018 (Versão 1803)<br/>➕ 10 Fall Creators Update (Versão 1709)<br/>➕ 10 Creators Update (Versão 1703)<br/>➕ 10 Atualização de Aniversário (Versão 1607)<br/>➕ 8.1<br/>➕|
|**Versões do Windows Server**|✔️ Windows Server 2019<br/>✔️ Windows Server, versão 1809<br/>✔️ Windows Server, versão 1803<br/>➕ Windows Server, versão 1709<br/>➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br/>– 461814 (Atualização de outubro de 2018 para o Windows 10)<br/>– 461808 (Atualização de abril de 2018 para o Windows 10 e Windows Server, versão 1803)<br/>- 461814 (todas as outras versões de sistema operacional)<br/>(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

<sup>1</sup> Requer a instalação do desenvolvimento de **desktop .NET, desenvolvimento** **de ASP.NET e web,** **desenvolvimento do Azure,** **desenvolvimento do Office/SharePoint,** desenvolvimento móvel com cargas de trabalho **de desenvolvimento de plataformas multiplataforma** **.NET**ou .NET Core.

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-471)
- [Novidades em acessibilidade](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Versões do Windows**|✔️ 10 Fall Creators Update (Versão 1709)<br/>➕ 10 Creators Update (Versão 1703)<br/>➕ 10 Atualização de Aniversário (Versão 1607)<br/>➕ 8.1<br/>➕|
|**Versões do Windows Server**|➕ Windows Server, versão 1803<br/>✔️ Windows Server, versão 1709<br/>➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br/>– 461308 (Atualização do Windows 10 para Criadores e Windows Server, versão 1709)<br/>– 461310 (todas as outras versões do SO)<br/>(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-47)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Versões do Windows**|✔️ 10 Creators Update (Versão 1703)<br/>➕ 10 Atualização de Aniversário (Versão 1607)<br/>➕ 8.1<br/>➕|
|**Versões do Windows Server**|➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br/>– 460798 (Atualização do Windows 10 para Criadores)<br/>– 460805 (todas as outras versões do sistema operacional)<br/>(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-462)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Versões do Windows**|✔️ 10 Atualização de Aniversário (Versão 1607)<br/>➕ Atualização de 10 de Novembro (Versão 1511)<br/>➕ 10<br/>➕ 8.1<br />7 ➕|
|**Versões do Windows Server**|✔️ 2016<br /><br/>➕ R2 2012<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br /><br/>– 394802 (Atualização de Aniversário do Windows 10 e Windows Server 2016)<br/>– 394806 (todas as outras versões de SO)<br /><br/>(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-461)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Incluída na versão do Visual Studio**|2017<sup>1</sup>|
|**Versões do Windows**|✔️ Atualização de 10 de Novembro (Versão 1511)<br/>➕ 10<br />➕ 8.1<br />➕ 8<br />7 ➕|
|**Versões do Windows Server**|➕ R2 2012<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br /><br/>– 394254 (Atualização de novembro do Windows 10)<br />– 394271 (todas as outras versões de SO)<br /><br/>(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

<sup>1</sup> Requer a instalação do desenvolvimento de **desktop .NET, desenvolvimento** **de ASP.NET e web,** **desenvolvimento do Azure,** **desenvolvimento do Office/SharePoint,** desenvolvimento móvel com cargas de trabalho **de desenvolvimento de plataformas multiplataforma** **.NET**ou .NET Core.

### <a name="net-framework-46"></a>.NET framework 4.6

- [Novos recursos](../whats-new/index.md#whats-new-in-net-2015)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Incluída na versão do Visual Studio**|2015|
|**Versões do Windows**|✔️ 10<br /><br />➕ 8.1<br />➕ 8<br />7 ➕<br />➕ Vista|
|**Versões do Windows Server**|➕ R2 2012<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ SP2 2008|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br /><br />– 393295 (Windows 10)<br />– 393297 (todas as outras versões de SO)<br /><br />(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-452)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Versões do Windows**|➕ 8.1<br />➕ 8<br />7 ➕<br />➕ Vista|
|**Versões do Windows Server**|➕ R2 2012<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ SP2 2008|
|**Para determinar a versão .NET instalada**|Use `Release` DWORD 379893<br /><br />(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-451)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Incluída na versão do Visual Studio**|2013|
|**Versões do Windows**|✔️ 8.1<br /><br />➕ 8<br />7 ➕<br />➕ Vista|
|**Versões do Windows Server**|✔️ R2 de 2012<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ SP2 2008|
|**Para determinar a versão .NET instalada**|Use DWORD `Release`:<br /><br />– 378675 (Windows 8.1)<br />– 378758 (todos os outros)<br /><br />(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Novos recursos](../whats-new/index.md#whats-new-in-net-framework-45)
- [Notas de versão](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Versão CLR**|4|
|**Incluída na versão do Visual Studio**|2012|
|**Versões do Windows**|✔️ 8<br />7 ➕<br />➕ Vista|
|**Versões do Windows Server**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ SP2 2008|
|**Para determinar a versão .NET instalada**|Use `Release` DWORD 378389<br /><br />(Veja [as instruções)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-4"></a>.NET Framework 4

[Novos recursos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Versão CLR**|4|
|**Incluída na versão do Visual Studio**|2010|
|**Versões do Windows**|7 ➕<br />➕ Vista|
|**Versões do Windows Server**|➕ 2008 R2 SP1<br />➕ SP2 2008<br />➕ 2003|
|**Para determinar a versão .NET instalada**|Ver [instruções](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3,5

[Novos recursos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- Árvores de expressão
- Suporte ASP.NET aprimorado para o desenvolvimento do AJAX
- Coleções HashSet
- DateTimeOffset
- Integração WCF e WF
- Rede peer-to-peer
- Complementos para extensibilidade

|||
|-|-|
|**Versão CLR**|2,0|
|**Incluída na versão do Visual Studio**|2008|
|**Versões do Windows**|✔️ 10\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Versões do Windows Server**|➕ Windows Server, versão 1803\*<br/>➕ Windows Server, versão 1709\*<br/>➕ 2016\*<br/>➕ R2 2012\*<br />➕ 2012\*<br /><br />✔️2008 R2 SP1\*<br /><br/>➕ SP2 2008<br />➕ 2003|
|**Para determinar a versão .NET instalada**|Ver [instruções](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Novos recursos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)):

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Espaço do Cartão do Windows

|||
|-|-|
|**Versão CLR**|2,0|
|**Versões do Windows**|✔️ Vista|
|**Versões do Windows Server**|✔️ 2008 R2 SP1*<br />✔️ SP2 2008\*<br /><br />➕ 2003|
|**Para determinar a versão .NET instalada**|Veja [instruções](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Novos recursos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29):

- Genéricos
- Editar e continuar depurador
- Escalabilidade e desempenho melhorados
- implantação ClickOnce
- Em ASP.NET 2.0, novos controles e suporte para uma ampla gama de navegadores
- Suporte a 64 bits

|||
|-|-|
|**Versão CLR**|2,0|
|**Incluída na versão do Visual Studio**|2005|
|**Versões do Windows**|N/D|
|**Versões do Windows Server**|✔️ 2008 R2 SP1<br />✔️ SP2 2008<br />✔️ 2003|
|**Para determinar a versão .NET instalada**|Ver [instruções](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Novos recursos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29):

- ASP.NET controles móveis
- Execução lado a lado
- Suporte a IPv6

|||
|-|-|
|**Versão CLR**|1,1|
|**Incluída na versão do Visual Studio**|2003|
|**Versões do Windows**|N/D|
|**Versões do Windows Server**|✔️ 2003|
|**Para determinar a versão .NET instalada**|Ver [instruções](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Versão CLR**|1.0|
|**Incluída na versão do Visual Studio**|Visual Studio .NET|
|**Versões do Windows**|N/D|
|**Versões do Windows Server**|N/D|
|**Para determinar a versão .NET instalada**|Ver [instruções](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - O Framework .NET deve ser ativado neste sistema operacional através do [Painel de Controle (para Windows) ou do Gerenciador de Servidores (para O Servidor Windows)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).
> - Em geral, você não deve desinstalar nenhuma versão do .NET Framework que esteja instalada no seu computador, porque um aplicativo que você usa pode depender de uma versão específica e pode quebrar se essa versão for removida. Você pode carregar várias versões do .NET Framework em um único computador ao mesmo tempo. Isso significa que você pode instalar o .NET Framework sem ter que desinstalar versões anteriores. Para obter mais informações, consulte [Getting Started](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Observações para a versão 4.5 e posterior

.NET Framework 4.5 é uma atualização no local que substitui o .NET Framework 4 no seu computador e, da mesma forma, o .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 e 4.8 são atualizações no local para o .NET Framework 4.5. Atualização no local significa que eles usam a mesma versão em tempo de execução, mas as versões de montagem são atualizadas e incluem novos tipos e membros. Depois de instalar uma dessas atualizações, os aplicativos .NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 ou .NET Framework 4.7 devem continuar em execução sem exigir recompilação. No entanto, o inverso não é verdadeiro. Não recomendamos a execução de aplicativos que visam uma versão posterior do .NET Framework em uma versão anterior. Por exemplo, não recomendamos executar um aplicativo que tenha o .NET Framework 4.6 como destino no .NET Framework 4.5.

As seguintes diretrizes se aplicam:

- No Visual Studio, você pode escolher o .NET Framework 4.5 como a estrutura de destino para um projeto (isso define a propriedade <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType>) para compilar o projeto como um assembly ou um executável do .NET Framework 4.5. Esse assembly ou executável pode ser usado em qualquer computador que tenha o .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8 instalado.

- No Visual Studio, você pode escolher o .NET Framework 4.5.1 como o framework de destino de um projeto para compilá-lo como um conjunto .NET Framework 4.5.1 ou executável. Execute apenas este conjunto ou executável em computadores que tenham o .NET Framework 4.5.1 ou posterior instalado. Um executável que tenha como alvo o .NET Framework 4.5.1 será impedido de ser executado em um computador que tenha apenas uma versão anterior do .NET Framework, como o .NET Framework 4.5, instalado. O usuário será solicitado a instalar o .NET Framework 4.5.1. Além disso, as assembléias do .NET Framework 4.5.1 não devem ser chamadas de um aplicativo que tenha como alvo uma versão anterior do .NET Framework, como o .NET Framework 4.5.

  > [!NOTE]
  > O .NET Framework 4.5.1 e o .NET Framework 4.5 são usados aqui apenas como exemplos. O princípio descrito se aplica a qualquer aplicativo que tenha como alvo uma versão posterior do .NET Framework do que a instalada no sistema em que está sendo executado.

Algumas alterações no .NET Framework podem exigir alterações no código do aplicativo; consulte [Compatibilidade de aplicativos](application-compatibility.md) antes de executar seus aplicativos existentes com versões .NET Framework 4.5 ou posteriores. Para obter mais informações sobre como instalar a versão atual, consulte [Instalar o .NET Framework para desenvolvedores](../install/guide-for-developers.md). Para obter informações sobre o suporte ao .NET Framework, consulte a [política oficial de suporte do .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) no site .NET.

## <a name="remarks-for-older-versions"></a>Observações para versões mais antigas

As versões 2.0, 3.0 e 3.5 do .NET Framework são integradas com a mesma versão do CLR (CLR 2.0). Essas versões representam camadas sucessivas de uma única instalação. Cada versão é compilada incrementalmente sobre as versões anteriores. Não é possível rodar as versões 2.0, 3.0 e 3.5 lado a lado em um computador. Ao instalar a versão 3.5, você obtém as camadas 2.0 e 3.0 automaticamente, e os aplicativos que foram criados para versões 2.0, 3.0 e 3.5 podem todos ser executados na versão 3.5. No entanto, o .NET Framework 4 encerra essa abordagem de camadas, e ele e versões posteriores (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 e 4.8) também representam camadas sucessivas de uma única instalação. Começando com o .NET Framework 4, você pode usar a hospedagem em processo, lado a lado, para executar várias versões do CLR em um único processo. Para saber mais, confira [Assemblies e execução lado a lado](../../standard/assembly/side-by-side-execution.md).

Além disso, se o aplicativo tiver como alvo a versão 2.0, 3.0 ou 3.5, seus usuários podem ser obrigados a ativar o .NET Framework 3.5 em um computador Windows 8, Windows 8.1 ou Windows 10 antes que eles possam executar o seu aplicativo. Para obter mais informações, consulte [Instalando o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Próximas etapas

- Se você não tem experiência com o .NET Framework, confira a [visão geral](../get-started/overview.md) para ver uma introdução aos principais conceitos e recursos.

- Para obter novos recursos e melhorias no .NET Framework 4.5 e suas versões de pontos, consulte [as novidades do Quadro .NET](../whats-new/index.md).

- Para obter informações sobre como migrar seu aplicativo para uma versão mais recente do .NET Framework, consulte o [guia de migração](index.md).

- Para saber mais sobre como determinar quais versões ou atualizações estão instaladas em um computador, confira [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md) (Como determinar quais versões do .NET Framework estão instaladas) e [How to: Determine Which .NET Framework Updates Are Installed](how-to-determine-which-net-framework-updates-are-installed.md) (Como determinar quais atualizações do .NET Framework estão instaladas).

## <a name="see-also"></a>Confira também

- [Compatibilidade de versão](version-compatibility.md)
| [.NET Framework política de suporte oficial](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
