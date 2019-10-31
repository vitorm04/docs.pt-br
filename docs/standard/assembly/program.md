---
title: Programar com assemblies
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
ms.openlocfilehash: 9f07d36d9e47189d53e367fd1406e5684c024aa3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107062"
---
# <a name="program-with-assemblies"></a>Programar com assemblies
Os assemblies são os blocos de construção do .NET Framework; eles formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança. Um assembly oferece ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo. Trata-se de uma coleção de tipos e recursos compilados para trabalharem juntos e formar uma unidade lógica de funcionalidade. Para o runtime, um tipo não existe fora do contexto de um assembly.  
  
 Esta seção descreve como criar módulos, criar assemblies usando módulos, criar um par de chaves e assinar um assembly com um nome forte, bem como instalar um assembly no cache de assembly global. Além disso, esta seção descreve como usar o [Desmontador de MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) para exibir informações do manifesto do assembly.  
  
> [!NOTE]
> A partir do .NET Framework versão 2.0, o runtime não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o runtime atualmente carregado. Isso vale para a combinação dos componentes principal e secundário do número de versão.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criar assemblies](create.md)  
 Fornece uma visão geral dos assemblies de arquivo único e vários arquivos.  
  
 [Nomes de assembly](names.md)  
 Fornece uma visão geral da nomenclatura de assembly.  
  
 [Como determinar o nome totalmente qualificado de um assembly](find-fully-qualified-name.md)  
 Descreve como determinar o nome totalmente qualificado de um assembly.  
  
 [Executar aplicativos de intranet com confiança total](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Descreve como especificar a política de segurança herdada para assemblies de confiança total em um compartilhamento de intranet.  
  
 [Local do assembly](location.md)  
 Fornece uma visão geral de onde localizar assemblies.  
  
 [Como criar um assembly de arquivo único](../../framework/app-domains/build-single-file-assembly.md)  
 Descreve como criar um assembly de arquivo único.  
  
 [Assemblies de multiarquivo](../../framework/app-domains/multifile-assemblies.md)  
 Descreve os motivos para a criação de assemblies de vários arquivos.  
  
 [Como compilar um assembly de multiarquivos](../../framework/app-domains/build-multifile-assembly.md)  
 Descreve como criar um assembly de vários arquivos.  
  
 [Definir atributos de assembly](set-attributes.md)  
 Descreve os atributos de assembly e como defini-los.  
  
 [Criar e usar assemblies de nome forte](create-use-strong-named.md)  
 Descreve como e por que assinar um assembly com um nome forte, além de inclui tópicos explicativos.  
  
 [Assinar um assembly com atraso](delay-sign.md)  
 Descreve como assinar um assembly com atraso.  
  
 [Trabalhar com assemblies e o cache de assembly global](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Descreve como e por que adicionar assemblies ao cache de assembly global, além de incluir tópicos explicativos.  
  
 [Como exibir o conteúdo do assembly](view-contents.md)  
 Descreve como usar o Desmontador de MSIL (Ildasm.exe) para exibir o conteúdo do assembly.  
  
 [Encaminhamento de tipo no Common Language Runtime](type-forwarding.md)  
 Descreve como usar encaminhamento de tipo para mover um tipo para um assembly diferente sem interromper aplicativos existentes.  
  
## <a name="reference"></a>Referência  
 <xref:System.Reflection.Assembly>  
 A classe do .NET Framework que representa um assembly.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como obter informações de tipo e membro de um assembly](../../framework/reflection-and-codedom/get-type-member-information.md)  
 Descreve como obter de modo programático o tipo e outras informações de um assembly.  
  
 [Assemblies no .NET](index.md)  
 Fornece uma visão geral conceitual dos assemblies de Common Language Runtime.  
  
 [Controle de versão do assembly](versioning.md)  
 Fornece uma visão geral de associação de assembly e dos atributos <xref:System.Reflection.AssemblyVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute>.  
  
 [Como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 Descreve como o runtime determina qual assembly usar para atender a uma solicitação de associação.  
  
 [Reflexão](../../framework/reflection-and-codedom/reflection.md)   
 Descreve como usar a classe **Reflection** para obter informações sobre um assembly.
