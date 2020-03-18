---
title: Nomes de assembly
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733105"
---
# <a name="assembly-names"></a>Nomes de assembly
Um nome de assembly é armazenado em metadados e tem um impacto significativo no escopo e uso do assembly por um aplicativo. Um assembly de nome forte tem um nome totalmente qualificado que inclui o nome, a cultura, a chave pública e o número de versão do assembly. Isso muitas vezes é chamado de nome de exibição, e para os assemblies carregados pode ser obtido usando a propriedade <xref:System.Reflection.Assembly.FullName%2A>.

 O runtime usa essas informações para localizar o assembly e diferenciá-lo de outros assemblies com o mesmo nome. Por exemplo, um assembly de nome forte chamado `myTypes` poderia ter o seguinte nome totalmente qualificado:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> A arquitetura do processador é adicionada à identidade do assembly na versão 2.0 do .NET Framework, para permitir versões específicas do processador de assemblies. Crie versões de um assembly cuja identidade varie apenas pela arquitetura do processador, por exemplo, versões específicas de processador 32 bits e 64 bits. A arquitetura do processador não é necessária para nomes fortes. Para obter mais informações, consulte <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Neste exemplo, o nome totalmente qualificado indica que o assembly `myTypes` tem um nome forte com um token de chave pública, tem o valor de cultura para inglês (EUA) e tem um número de versão de 1.0.1234.0. A arquitetura de seu processador é "msil", que significa que ele será compilado no modo JIT (just-in-time) para códigos de 32 bits ou 64 bits dependendo do sistema operacional e do processador.

 O código que solicita tipos em um assembly deve usar um nome totalmente qualificado do assembly. Isso é chamado de associação totalmente qualificada. A associação parcial, que especifica um nome de assembly, não tem permissão ao fazer referência a assemblies no .NET Framework.

 Todas as referências de montagem às assembléias que compõem o Quadro .NET também devem conter o nome totalmente qualificado da montagem. Por exemplo, uma referência ao conjunto System.Data .NET Framework para a versão 1.0 incluiria:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Observe que a versão corresponde ao número de versão de todos os assemblies do .NET Framework que acompanham o .NET Framework versão 1.0. Para assemblies do .NET Framework, o valor da cultura é sempre neutro, e a chave pública é a mesma mostrada no exemplo acima.

 Por exemplo, para adicionar uma referência de assembly em um arquivo de configuração a fim de configurar um ouvinte de rastreamento, você incluiria o nome totalmente qualificado do assembly do .NET Framework do sistema:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> O runtime trata nomes de assembly sem diferenciar maiúsculas de minúsculas ao associar a um assembly, mas preserva qualquer caso usado em um nome de assembly. Várias ferramentas no SDK do Windows lidam com nomes de assembly diferenciando maiúsculas de minúsculas. Para obter melhores resultados, gerencie nomes de assembly como se diferenciassem maiúsculas de minúsculas.

## <a name="name-application-components"></a>Componentes do aplicativo de nome
 O runtime não considera o nome do arquivo ao determinar a identidade de um assembly. A identidade do assembly, composta pelo nome, versão, cultura e nome forte do assembly, deve ficar clara para o runtime.

 Por exemplo, se você tiver uma assembléia chamada *myAssembly.exe* que faz referência a uma assembléia chamada *myAssembly.dll,* a vinculação ocorrerá corretamente se você executar *myAssembly.exe*. No entanto, se outro aplicativo executar o <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> *myAssembly.exe* usando o método, o tempo de `myAssembly`execução determina que `myAssembly` já está carregado quando o *myAssembly.exe* solicita vinculação a . Neste caso, *o myAssembly.dll* nunca está carregado. Como *o myAssembly.exe* não contém o <xref:System.TypeLoadException> tipo solicitado, ocorre um.

 Para evitar esse problema, verifique se os assemblies que compõem seu aplicativo não têm o mesmo nome de assembly ou colocam assemblies com o mesmo nome em diretórios diferentes.

> [!NOTE]
> No Quadro .NET, se você colocar um conjunto com nome forte no cache de montagem global, o nome do arquivo da montagem deve corresponder ao nome do conjunto, sem incluir a extensão do nome do arquivo, como *.exe* ou *.dll*. . Por exemplo, se o nome do arquivo de um conjunto for `myAssembly` *myAssembly.dll*, o nome de montagem deve ser . Assemblies particulares implantados somente no diretório do aplicativo raiz podem ter um nome de assembly diferente do nome do arquivo.

## <a name="see-also"></a>Confira também

- [Como: Determinar o nome totalmente qualificado de uma assembléia](find-fully-qualified-name.md)
- [Criar assemblies](create.md)
- [Assembléias com nomes fortes](strong-named.md)
- [Cache de montagem global](../../framework/app-domains/gac.md)
- [Como o tempo de execução localiza conjuntos](../../framework/deployment/how-the-runtime-locates-assemblies.md)
