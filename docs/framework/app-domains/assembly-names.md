---
title: Nomes de assembly
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9e1ba7e92614eab4d94fe953e5a0ae19611604f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927975"
---
# <a name="assembly-names"></a>Nomes de assembly
Um nome de assembly é armazenado em metadados e tem um impacto significativo no escopo e uso do assembly por um aplicativo. Um assembly de nome forte tem um nome totalmente qualificado que inclui o nome, a cultura, a chave pública e o número de versão do assembly. Isso muitas vezes é chamado de nome de exibição, e para os assemblies carregados pode ser obtido usando a propriedade <xref:System.Reflection.Assembly.FullName%2A>.  
  
 O tempo de execução usa essas informações para localizar o assembly e diferenciá-lo de outros assemblies com o mesmo nome. Por exemplo, um assembly de nome forte chamado `myTypes` poderia ter o seguinte nome totalmente qualificado:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
> A arquitetura do processador é adicionada à identidade do assembly na versão 2.0 do .NET Framework, para permitir versões específicas do processador de assemblies. Crie versões de um assembly cuja identidade varie apenas pela arquitetura do processador, por exemplo, versões específicas de processador 32 bits e 64 bits. A arquitetura do processador não é necessária para nomes fortes. Para obter mais informações, consulte <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 Neste exemplo, o nome totalmente qualificado indica que o assembly `myTypes` tem um nome forte com um token de chave pública, tem o valor de cultura para inglês (EUA) e tem um número de versão de 1.0.1234.0. A arquitetura de seu processador é "msil", que significa que ele será compilado no modo JIT (just-in-time) para códigos de 32 bits ou 64 bits dependendo do sistema operacional e do processador.  
  
 O código que solicita tipos em um assembly deve usar um nome totalmente qualificado do assembly. Isso é chamado de associação totalmente qualificada. A associação parcial, que especifica um nome de assembly, não tem permissão ao fazer referência a assemblies no .NET Framework.  
  
 Todas as referências de assembly para os assemblies que compõem o .NET Framework também devem conter um nome totalmente qualificado do assembly. Por exemplo, para fazer referência ao assembly System.Data.NET Framework para a versão 1.0 você incluiria:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Observe que a versão corresponde ao número de versão de todos os assemblies do .NET Framework que acompanham o .NET Framework versão 1.0. Para assemblies do .NET Framework, o valor da cultura é sempre neutro, e a chave pública é a mesma mostrada no exemplo acima.  
  
 Por exemplo, para adicionar uma referência de assembly em um arquivo de configuração a fim de configurar um ouvinte de rastreamento, você incluiria o nome totalmente qualificado do assembly do .NET Framework do sistema:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
> O tempo de execução trata nomes de assembly sem diferenciar maiúsculas de minúsculas ao associar a um assembly, mas preserva qualquer caso usado em um nome de assembly. Várias ferramentas no SDK do Windows lidam com nomes de assembly diferenciando maiúsculas de minúsculas. Para obter melhores resultados, gerencie nomes de assembly como se diferenciassem maiúsculas de minúsculas.  
  
## <a name="naming-application-components"></a>Nomenclatura de componentes do aplicativo  
 O tempo de execução não considera o nome do arquivo ao determinar a identidade de um assembly. A identidade do assembly, composta pelo nome, versão, cultura e nome forte do assembly, deve ficar clara para o tempo de execução.  
  
 Por exemplo, se você tiver um assembly denominado myAssembly.exe que faz referência a um assembly denominado myAssembly.dll, a associação ocorrerá corretamente se você executar myAssembly.exe. No entanto, se outro aplicativo executar myAssembly.exe usando o método <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, o tempo de execução determinará que "myAssembly" já está carregado quando myAssembly.exe solicitar a associação ao "myAssembly". Nesse caso, myAssembly.dll nunca é carregado. Como myAssembly.exe não contém o tipo solicitado, ocorrerá uma <xref:System.TypeLoadException>.  
  
 Para evitar esse problema, verifique se os assemblies que compõem seu aplicativo não têm o mesmo nome de assembly ou colocam assemblies com o mesmo nome em diretórios diferentes.  
  
> [!NOTE]
> Se você colocar um assembly de nome forte no cache de assembly global, o nome de arquivo do assembly deverá corresponder ao nome de assembly (não incluindo a extensão de nome de arquivo, como .exe ou .dll). Por exemplo, se o nome do arquivo de um assembly for myAssembly.dll, o nome do assembly deverá ser myAssembly. Assemblies particulares implantados somente no diretório do aplicativo raiz podem ter um nome de assembly diferente do nome do arquivo.  
  
## <a name="see-also"></a>Consulte também

- [Como: Determinar o nome totalmente qualificado de um assembly](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)
- [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)
- [Assemblies de nomes fortes](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Cache de assembly global](../../../docs/framework/app-domains/gac.md)
- [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
