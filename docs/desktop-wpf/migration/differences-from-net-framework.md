---
title: Diferenças entre .NET Framework e .NET Core
description: Descreve as diferenças entre a implementação do .NET Framework da Windows Presentation Foundation (WPF) e o .NET Core WPF. Ao migrar seu aplicativo, você deve considerar essas incompatibilidades.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072203"
---
# <a name="differences-in-wpf"></a>Diferenças no WPF

Este artigo descreve as diferenças entre o Windows Presentation Foundation (WPF) no .NET Core e no .NET Framework. WPF for .NET Core é uma [estrutura de código aberto bifurcada](https://github.com/dotnet/wpf) do Código Fonte .NET original para o código-fonte do .NET Framework.

Existem alguns recursos do .NET Framework que o .NET Core não suporta. Para obter mais informações sobre tecnologias não suportadas, consulte [as tecnologias .NET Framework indisponíveis no .NET Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projetos no estilo SDK

O .NET Core usa arquivos de projeto no estilo SDK. Esses arquivos de projeto são diferentes dos arquivos tradicionais do projeto .NET Framework gerenciados pelo Visual Studio. Para migrar seus aplicativos .NET Framework WPF para .NET Core, você deve converter seus projetos. Para obter mais informações, consulte [migrar aplicativos WPF para .NET Core 3.0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Referências do pacote NuGet

Se o aplicativo .NET Framework listar suas dependências do NuGet em [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) um arquivo *packages.config,* migrará para o formato:

1. No Visual Studio, abra o painel **Solution Explorer.**
1. No projeto WPF, clique com o botão direito **do mouse.config** > **Migrate packages.config to PackageReference**.

![Atualizando para o PackageReference](media/differences-from-net-framework/package-reference-migration.png)

Um diálogo aparecerá mostrando dependências nuget calculadas de alto nível e perguntando quais outros pacotes NuGet devem ser promovidos para o nível superior. Selecione **OK** e o arquivo *packages.config* `<PackageReference>` será removido do projeto e os elementos serão adicionados ao arquivo do projeto.

Quando o `<PackageReference>`seu projeto usa, os pacotes não são armazenados localmente em uma pasta *Pacotes,* eles são armazenados globalmente. Abra o arquivo do `<Analyzer>` projeto e remova todos os elementos referentes à pasta *Pacotes.* Esses analisadores são automaticamente incluídos nas referências do pacote NuGet.

## <a name="code-access-security"></a>Segurança de Acesso do Código

O CAS (Code Access Security, segurança de acesso ao código) não é suportado pelo .NET Core ou pelo WPF for .NET Core. Todas as funcionalidades relacionadas ao CAS são tratadas sob a suposição de total confiança. O WPF for .NET Core remove o código relacionado ao CAS. A superfície pública de API desses tipos ainda existe para garantir que as chamadas para esses tipos tenham sucesso.

Os tipos relacionados ao CAS definidos publicamente foram movidos para fora das assembléias do WPF e para as assembléias de bibliotecas Core .NET. Os conjuntos WPF têm um conjunto de encaminhamento de tipo para a nova localização dos tipos movidos.

| Montagem de origem | Montagem de alvo | Type                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Para minimizar o atrito de portação, a funcionalidade para armazenar e recuperar informações relacionadas às seguintes propriedades foi mantida no `XamlAccessLevel` tipo.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Próximas etapas

- [Saiba como portar um aplicativo .NET Framework WPF para .NET Core.](convert-project-from-net-framework.md)
