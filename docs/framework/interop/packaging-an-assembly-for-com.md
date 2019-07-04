---
title: Empacotando um assembly para o COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6933aa5ee253f78806aba401749256934f490126
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833583"
---
# <a name="packaging-an-assembly-for-com"></a>Empacotando um assembly para o COM

Desenvolvedores COM podem aproveitar as informações a seguir sobre os tipos gerenciados que pretendem incorporar em seus aplicativos:

- Uma lista de tipos que aplicativos COM podem consumir

  Alguns tipos gerenciados são visíveis para COM; alguns são visíveis, mas não instanciável; e alguns são visíveis e instanciáveis. Um assembly pode incluir qualquer combinação de tipos invisíveis, visíveis, não instanciáveis e instanciáveis. Para fins de integridade, identifique os tipos em um assembly que você pretende expor ao COM, especialmente quando esses tipos são um subconjunto dos tipos expostos ao .NET Framework.

  Para obter mais informações, consulte [Qualificando tipos do .NET para interoperação](qualifying-net-types-for-interoperation.md).

- Instruções de controle de versão

  Classes gerenciadas que implementam a interface de classe (uma interface gerada por interoperabilidade COM) estão sujeitas a restrições de controle de versão.

  Para obter diretrizes de como usar a interface de classe, consulte [Introdução à interface de classe](com-callable-wrapper.md#introducing-the-class-interface).

- Instruções de implantação

  Assemblies de nome forte que são assinados por um editor podem ser instalados no cache de assembly global. Assemblies não assinados devem ser instalados no computador do usuário como assemblies particulares.

  Para obter mais informações, consulte [Considerações sobre segurança de assembly](../app-domains/assembly-security-considerations.md).

- Inclusão de biblioteca de tipos

  A maioria dos tipos requerem uma biblioteca de tipos quando consumidos por um aplicativo COM. Você pode gerar uma biblioteca de tipos ou fazer com que desenvolvedores COM executem essa tarefa. O SDK (Software Development Kit) do Windows fornece as seguintes opções para gerar uma biblioteca de tipos:

  - [Exportador da Biblioteca de Tipos](#cpconpackagingassemblyforcomanchor1)

  - [Classe TypeLibConverter](#cpconpackagingassemblyforcomanchor2)

  - [Ferramenta de Registro de Assembly](#cpconpackagingassemblyforcomanchor3)

  - [Ferramenta de Instalação de Serviços .NET](#cpconpackagingassemblyforcomanchor4)

  Independentemente do mecanismo escolhido, somente os tipos públicos definidos no assembly que você fornecer são incluídos na biblioteca de tipos gerada.

  Você pode empacotar uma biblioteca de tipos como um arquivo separado ou inseri-la como arquivo de recurso Win32 dentro de um aplicativo baseado em .NET. Microsoft Visual Basic 6.0 executou essa tarefa para você automaticamente. No entanto, ao usar [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], você deve inserir manualmente sua biblioteca de tipos. Para obter instruções, veja [Como: Inserir bibliotecas de tipos como recursos do Win32 em aplicativos baseados no .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>Exportador da Biblioteca de Tipos

O [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em um assembly em uma biblioteca de tipos COM. Quando as informações de tipo da classe estão disponíveis, os clientes COM podem criar uma instância da classe do .NET e chamar os métodos da instância, como se fosse um objeto COM. Tlbexp.exe converte um assembly inteiro de uma vez. Não é possível usar Tlbexp.exe para gerar informações de tipo para um subconjunto dos tipos definidos em um assembly.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>Classe TypeLibConverter

A classe <xref:System.Runtime.InteropServices.TypeLibConverter>, localizada no namespace **System.Runtime.Interop**, converte as classes e interfaces contidas em um assembly em uma biblioteca de tipos COM. Essa API produz as mesmas informações que o Exportador da Biblioteca de Tipos, descrito na seção anterior.

A **classe TypeLibConverter** implementa o <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Ferramenta de Registro de Assembly

A [Ferramenta de Registro de Assembly (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) pode gerar e registrar uma biblioteca de tipos quando você aplica a opção **/tlb:** . Clientes COM exigem que as bibliotecas de tipos sejam instaladas no Registro do Windows. Sem essa opção, o Regasm.exe registra somente os tipos em um assembly, mas não a biblioteca de tipos. Registrar os tipos em um assembly e registrando a biblioteca de tipos são atividades distintas.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>Ferramenta de Instalação de Serviços .NET

A [ferramenta de instalação de serviços .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adiciona classes gerenciadas para Serviços do Componente do Windows 2000 e combina várias tarefas em uma única ferramenta. Além de carregar e registrar um assembly, Regsvcs.exe pode gerar, registrar e instalar a biblioteca de tipos em um aplicativo COM+ 1.0 existente.

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [Expondo componentes do .NET Framework ao COM](exposing-dotnet-components-to-com.md)
- [Qualificando tipos .NET para interoperação](qualifying-net-types-for-interoperation.md)
- [Apresentando a interface de classe](com-callable-wrapper.md#introducing-the-class-interface)
- [Considerações sobre segurança de assembly](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (Exportador de Biblioteca de Tipos)](../tools/tlbexp-exe-type-library-exporter.md)
- [Registrando assemblies usando COM](registering-assemblies-with-com.md)
- [Como: Inserir bibliotecas de tipos como recursos do Win32 em aplicativos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
