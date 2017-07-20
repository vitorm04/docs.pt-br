---
title: "Como gerenciar versões de dependência de pacote para .NET Core 1.0 | Microsoft Docs"
description: "Como gerenciar versões de dependência de pacote para o .NET Core 1.0"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 3576fecfd4964bc0a4ca9482888cd61e6ac44350
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

<a id="how-to-manage-package-dependency-versions-for-net-core-10" class="xliff"></a>

# Como gerenciar versões de dependência de pacote para o .NET Core 1.0

Esse artigo aborda o que você precisa saber sobre as versões do pacote para seus aplicativos e bibliotecas .NET Core.

<a id="glossary" class="xliff"></a>

## Glossário

**Corrigir** – Corrigir as dependências significa que você está usando a mesma “família” de pacotes lançados em NuGet para .NET Core 1.0.

**Metapacote** – Um pacote NuGet que representa um conjunto de pacotes NuGet.

**Cortar** – O ato de remover de um metapacote os pacotes dos quais você não.  Isso é algo relevante para autores de pacotes NuGet.  Consulte [Reduzindo as dependências de pacote com o project.json](../deploying/reducing-dependencies.md) para obter mais informações. 

<a id="fix-your-dependencies-to-net-core-10" class="xliff"></a>

## Corrija suas dependências para o .NET Core 1.0

Para restaurar os pacotes de forma confiável e escrever código com segurança, é importante que você corrija suas dependências para as versões de pacotes enviados juntamente com o .NET Core 1.0.  Isso significa que todos os pacotes devem ter uma única versão sem nenhum qualificador adicional.

**Exemplos de pacotes corrigidos para 1.0**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**Exemplos de pacotes NÃO corrigidos para 1.0**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

<a id="why-does-this-matter" class="xliff"></a>

### Por que isso importa?

Asseguramos que, se você corrigir suas dependências para aquelas fornecidas junto com o .NET Core 1.0, os pacotes sempre funcionarão juntos.  Essa garantia não existe se você usar pacotes que não são corrigidos dessa maneira.

<a id="scenarios" class="xliff"></a>

### Cenários

Embora haja uma grande lista de todos os pacotes e suas versões lançadas com o .NET Core 1.0, você pode não precisar examiná-la se seu código estiver em determinados cenários.

**Você tem somente dependências de** `NETStandard.Library`**?**

Se assim, você deve corrigir o pacote `NETStandard.Library` para a versão `1.6`.  Como esse é um metapacote auxiliar, o fechamento do seu pacote também é corrigido para 1.0.

**Você tem somente dependências de** `Microsoft.NETCore.App`**?**

Se assim, você deve corrigir o pacote `Microsoft.NETCore.App` para a versão `1.0.0`.  Como esse é um metapacote auxiliar, o fechamento do seu pacote também é corrigido para 1.0.

**Você está [cortando](../deploying/reducing-dependencies.md) as dependências do seu metapacote**  `NETStandard.Library` **ou** `Microsoft.NETCore.App` **?**

Nesse caso, você deve garantir que o metapacote de início seja corrigido para 1.0.  Os pacotes individuais dos quais você depende após o corte também são corrigidos para 1.0.

**Você tem dependências de pacotes fora dos metapacotes** `NETStandard.Library` **ou** `Microsoft.NETCore.App` **?**

Nesse caso, você precisa corrigir suas outras dependências para 1.0.  Consulte as versões do pacote correto e números de build no fim desse artigo.

<a id="a-note-on-using-a-splat-string--when-versioning" class="xliff"></a>

### Uma observação sobre o uso de uma cadeia de caracteres splat (\*) durante o controle de versão

Você pode ter adotado um padrão de controle de versão que usa uma cadeia de caracteres splat (\*) como esta: `"System.Collections":"4.0.11-*"`.

**Você não deve fazer isso**.  Usar a cadeia de caracteres splat pode resultar na restauração de pacotes de diferentes versões, algumas muito mais avançadas que o .NET Core 1.0.  Isso poderia deixar alguns pacotes incompatíveis.

<a id="packages-and-version-numbers-organized-by-metapackage" class="xliff"></a>

## Pacotes e os Números de Versão organizados por Metapacote

[Lista de todos os pacotes de biblioteca do .NET Standard e suas versões para 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Lista de todos os pacotes de tempo de execução e suas versões para 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Lista de todos os pacotes de aplicativo do .NET Core e suas versões para 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).

