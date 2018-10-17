---
title: Nomenclatura forte e bibliotecas do .NET
description: Práticas recomendadas para bibliotecas do .NET de nomeação forte.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: e3f7d443eb9acc84c800ea2611b803733085391c
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372798"
---
# <a name="strong-naming"></a>Nomenclatura forte

Nomenclatura forte refere-se ao assinar um assembly com uma chave, produzindo uma [assembly de nome forte](../../framework/app-domains/strong-named-assemblies.md). Quando um assembly é o nome forte, ele cria uma identidade exclusiva com base no número de versão de nome e o assembly, e ele pode ajudar a evitar conflitos de assembly.

A desvantagem de nomenclatura forte é que o .NET Framework no Windows permite estrito carregamento de assemblies depois que um assembly um nome forte. Uma referência de assembly de nome forte deve corresponder exatamente a versão referenciada por um assembly, forçar os desenvolvedores a [configurar redirecionamentos de associação](../../framework/configure-apps/redirect-assembly-versions.md) ao usar o assembly:

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Quando os desenvolvedores de .NET reclamarem sobre nomenclatura forte, o que eles reclamar sobre geralmente é estrito carregamento do assembly. Felizmente, esse problema é isolado para o .NET Framework. A maioria das outras implementações do .NET, Xamarin, UWP e .NET core não tiver o carregamento do assembly estrito e remove a principal desvantagem da nomenclatura forte.

Um aspecto importante da nomenclatura forte é que ele é viral: um nome forte assembly só podem fazer referência outros forte conjuntos nomeados. Se sua biblioteca não é forte nomeado, você excluiu os desenvolvedores que estão criando um aplicativo ou uma biblioteca que precisa de nomenclatura forte de usá-lo.

Os benefícios da nomenclatura forte são:

1. O assembly pode ser referenciado e usado por outros assemblies de nome forte.
2. O assembly pode ser armazenado no Cache de Assembly Global (GAC).
3. O assembly pode ser carregado lado a lado com outras versões do assembly. Carregamento do assembly lado a lado é normalmente exigido por aplicativos com arquiteturas de plug-in.

## <a name="create-strong-named-net-libraries"></a>Crie um forte chamado bibliotecas do .NET

Forte, você deve nomear suas bibliotecas do .NET de código-fonte aberto. Um assembly de nomenclatura forte garante que a maioria das pessoas pode usá-lo e estrito assembly carregar somente afeta o .NET Framework.

> [!NOTE]
> Neste guia é específico para bibliotecas .NET distribuídas publicamente, como bibliotecas .NET publicados em NuGet.org. Nomenclatura forte não é exigido pela maioria dos aplicativos .NET e não deve ser feita por padrão.

**Considere a possibilidade de ✔️** forte nomear os assemblies da sua biblioteca.

**Considere a possibilidade de ✔️** fazer check-in a chave usada para o nome forte em seu sistema de controle de origem.

> Uma chave disponível publicamente permite aos desenvolvedores modificar e recompilar seu código-fonte de biblioteca com a mesma chave.

> [!IMPORTANT]
> Quando uma identidade de criptografia for desejada, [Authenticode](/windows-hardware/drivers/install/authenticode) e [assinatura de pacote do NuGet](/nuget/create-packages/sign-a-package) são recomendados. Nomenclatura forte não deve ser usado para considerações de segurança.

**Considere a possibilidade de ✔️** incrementar a versão do assembly nas alterações de versão principal somente para ajudar os usuários a reduzir os redirecionamentos de associação e a frequência com que eles sejam atualizados.

> Leia mais sobre [controle de versão e a versão do assembly](./versioning.md#assembly-version).

**❌ NÃO** adicionar, remover ou alterar a chave de nomeação forte.

> Modificando a chave de nomenclatura forte do assembly é alterado na identidade do assembly e interrompe o código compilado que o utiliza. Para obter mais informações, consulte [binário alterações significativas](./breaking-changes.md#binary-breaking-change).

**❌ NÃO** publicar versões de nome forte e sem nome forte da biblioteca. Por exemplo, `Contoso.Api` e `Contoso.Api.StrongNamed`.

> Publicando duas bifurcações de pacotes em seu sistema de eco do desenvolvedor. Além disso, se um aplicativo acaba dependendo de ambos os pacotes de desenvolvedor pode encontrar conflitos de nome de tipo. Que diz respeito ao .NET são tipos diferentes em diferentes assemblies.

>[!div class="step-by-step"]
[Anterior](./cross-platform-targeting.md)
[Próximo](./nuget.md)
