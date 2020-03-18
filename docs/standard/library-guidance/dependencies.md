---
title: Dependências e bibliotecas do .NET
description: Melhores práticas para gerenciar as dependências do NuGet em bibliotecas do .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731485"
---
# <a name="dependencies"></a>Dependências

A principal maneira de adicionar as dependências em uma biblioteca do .NET fazer referência a pacotes do NuGet. Referências de pacote do NuGet permitem que você rapidamente reutilize e aproveite a funcionalidade já escrita, mas são uma fonte comum de atrito para desenvolvedores do .NET. Gerenciar dependências corretamente é importante para evitar que alterações em outras bibliotecas .NET provoquem falhas na sua biblioteca do .NET e vice-versa.

## <a name="diamond-dependencies"></a>Dependências de losango

É uma situação comum um projeto do .NET ter várias versões de um pacote em sua árvore de dependência. Por exemplo, um aplicativo depende de dois pacotes do NuGet e cada um dos quais depende de versões diferentes do mesmo pacote. Agora existe uma dependência de losango no grafo de dependência do aplicativo.

![Dependência de diamantes](./media/dependencies/diamond-dependency.png "Dependência de diamantes")

No momento da compilação, o NuGet analisa todos os pacotes de que um projeto depende, incluindo as dependências das dependências. Quando várias versões de um pacote são detectadas, as regras são avaliadas para escolher uma. Unificar pacotes é necessário porque executar versões lado a lado de um assembly no mesmo aplicativo é um problema no .NET.

A maioria das dependências de losangos é facilmente resolvida. No entanto, podem criar problemas em determinadas circunstâncias:

1. **Referências de pacote do NuGet conflitantes** impedem que uma versão seja resolvida durante a restauração de pacote.
2. **Alterações da falha entre as versões** causam erros e exceções em runtime.
3. **O assembly do pacote tem um nome forte**, a versão do assembly é alterada e o aplicativo está em execução no .NET Framework. Redirecionamentos de associação de assembly são necessários.

Não é possível saber quais pacotes serão usados junto com o seu. Uma boa maneira de reduzir a probabilidade de uma dependência de losango provocar falha na sua biblioteca é minimizar o número de pacotes dos quais você depende.

✔️ FAÇA a análise da sua biblioteca do .NET quanto a dependências desnecessárias.

## <a name="nuget-dependency-version-ranges"></a>Intervalos de versão de dependência do NuGet

Uma referência de pacote especifica o intervalo de pacotes válidos que ela permite. Normalmente, a versão de referência de pacote no arquivo de projeto é a versão mínima e não há um máximo.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

As regras que o NuGet usa ao resolver as dependências são [complexas](/nuget/consume-packages/dependency-resolution), mas o NuGet procura sempre a versão mais antiga aplicável. O NuGet prefere a versão mais antiga aplicável, em vez de usar a mais alta disponível, porque a mais baixa terá menos problemas de compatibilidade.

Devido à regra de versão mais baixa aplicável do NuGet, não é necessário colocar uma versão superior ou o intervalo exato em referências de pacote para evitar obter a versão mais recente. O NuGet já tenta encontrar a versão mais baixa e mais compatível para você.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Limites de versão superior fará com que o NuGet falhe se houver um conflito. Por exemplo, uma biblioteca aceita exatamente 1.0, enquanto a outra biblioteca exige 2.0 ou superior. Embora alterações da falha possam ter sido introduzidas na versão 2.0, uma dependência de versão do limite superior ou estrita garantirá um erro.

![Conflito de dependência de diamantes](./media/dependencies/diamond-dependency-conflict.png "Conflito de dependência de diamantes")

❌NÃO tenha referências de pacote NuGet sem versão mínima.

❌EVITE referências do pacote NuGet que exigem uma versão exata.

❌EVITE as referências do pacote NuGet com um limite superior da versão.

## <a name="nuget-shared-source-packages"></a>Pacotes de código-fonte compartilhado do NuGet

Uma maneira de reduzir as dependências externas do pacote NuGet é fazer referência a pacotes de origem compartilhados. Um pacote de origem compartilhado contém [arquivos de código-fonte](/nuget/reference/nuspec#including-content-files) incluídos em um projeto quando referenciados. Como você está apenas incluindo arquivos de código-fonte compilados com o restante do seu projeto, não há dependência externa nem chance de conflito.

Pacotes de origem compartilhados são ótimos para incluir pequenas funcionalidades. Por exemplo, um pacote origem compartilhado de métodos auxiliares para fazer chamadas HTTP.

![Pacote de origem compartilhada](./media/dependencies/shared-source-package.png "Pacote de origem compartilhada")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Projeto de origem compartilhada](./media/dependencies/shared-source-project.png "Projeto de origem compartilhada")

Pacotes de origem compartilhado têm algumas limitações. Eles só podem ser referenciados por `PackageReference`, portanto, projetos `packages.config` mais antigos são excluídos. Também pacotes de origem compartilhados somente são utilizáveis por projetos com o mesmo tipo de linguagem. Devido a essas limitações, pacotes de origem compartilhados são melhor usados para compartilhar a funcionalidade dentro de um projeto de código-fonte aberto.

✔️ CONSIDERE fazer referência a de código-fonte compartilhados para pequenas funcionalidades internas.

✔️ CONSIDERE tornar seu pacote de um pacote de origem compartilhado se ele oferecer pequenas funcionalidades internas.

✔️ FAÇA referência a pacotes de origem compartilhados com `PrivateAssets="All"`.

> Essa configuração informa que o pacote do NuGet deve ser usado apenas no tempo de desenvolvimento e não deve ser exposto como uma dependência pública.

❌NÃO tenha tipos de pacotes de origem compartilhados em sua API pública.

> Tipos de origem compartilhada são compilados no assembly de referência e não podem ser trocados entre os limites de assembly. Por exemplo, um tipo `IRepository` de origem compartilhada em um projeto é um tipo separado do mesmo `IRepository` de origem compartilhada em outro projeto. Tipos em pacotes de origem compartilhados devem ter uma visibilidade `internal`.

❌NÃO publique pacotes de origem compartilhada para NuGet.org.

> Pacotes de origem compartilhados contêm código-fonte e só podem ser usados por projetos com o mesmo tipo de linguagem. Por exemplo, um pacote de origem compartilhado em C# não pode ser usado por um aplicativo em F#.
>
> Publicar pacotes de origem compartilhados em um [feed local ou no MyGet](./publish-nuget-package.md) para consumi-los internamente dentro de seu projeto.

>[!div class="step-by-step"]
>[Próximo](nuget.md)
>[anterior](sourcelink.md)
