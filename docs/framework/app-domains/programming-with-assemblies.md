---
title: "Programação com assemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 368021062a3ad49d2c63f92797c59b8c0f1cddfc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="programming-with-assemblies"></a>Programação com assemblies
Os assemblies são os blocos de construção do .NET Framework; eles formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança. Um assembly oferece ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo. Trata-se de uma coleção de tipos e recursos compilados para trabalharem juntos e formar uma unidade lógica de funcionalidade. Para o tempo de execução, um tipo não existe fora do contexto de um assembly.  
  
 Esta seção descreve como criar módulos, criar assemblies usando módulos, criar um par de chaves e assinar um assembly com um nome forte, bem como instalar um assembly no cache de assembly global. Além disso, esta seção descreve como usar o [Desmontador de MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir informações do manifesto do assembly.  
  
> [!NOTE]
>  A partir do .NET Framework versão 2.0, o tempo de execução não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o tempo de execução atualmente carregado. Isso vale para a combinação dos componentes principal e secundário do número de versão.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)  
 Fornece uma visão geral dos assemblies de arquivo único e vários arquivos.  
  
 [Nomes de assembly](../../../docs/framework/app-domains/assembly-names.md)  
 Fornece uma visão geral da nomenclatura de assembly.  
  
 [Como determinar o nome totalmente qualificado de um assembly](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Descreve como determinar o nome totalmente qualificado de um assembly.  
  
 [Execução de aplicativos de intranet em confiança total](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Descreve como especificar a política de segurança herdada para assemblies de confiança total em um compartilhamento de intranet.  
  
 [Local do assembly](../../../docs/framework/app-domains/assembly-location.md)  
 Fornece uma visão geral de onde localizar assemblies.  
  
 [Como compilar um assembly de arquivo único](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Descreve como criar um assembly de arquivo único.  
  
 [Assemblies de vários arquivos](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Descreve os motivos para a criação de assemblies de vários arquivos.  
  
 [Como Compilar um Assembly de Vários Arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Descreve como criar um assembly de vários arquivos.  
  
 [Configuração de atributos de assembly](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Descreve os atributos de assembly e como defini-los.  
  
 [Criando e usando assemblies com nome forte](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Descreve como e por que assinar um assembly com um nome forte, além de inclui tópicos explicativos.  
  
 [Assinar um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Descreve como assinar um assembly com atraso.  
  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Descreve como e por que adicionar assemblies ao cache de assembly global, além de incluir tópicos explicativos.  
  
 [Como exibir o conteúdo do assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Descreve como usar o Desmontador de MSIL (Ildasm.exe) para exibir o conteúdo do assembly.  
  
 [Encaminhamento de tipo no Common Language Runtime](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Descreve como usar encaminhamento de tipo para mover um tipo para um assembly diferente sem interromper aplicativos existentes.  
  
## <a name="reference"></a>Referência  
 <xref:System.Reflection.Assembly>  
 A classe do .NET Framework que representa um assembly.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como obter as informações de tipo e membro de um assembly](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Descreve como obter de modo programático o tipo e outras informações de um assembly.  
  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fornece uma visão geral conceitual dos assemblies de Common Language Runtime.  
  
 [Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md)  
 Fornece uma visão geral de associação de assembly e dos atributos <xref:System.Reflection.AssemblyVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute>.  
  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Descreve como o tempo de execução determina qual assembly usar para atender a uma solicitação de associação.  
  
 [Reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Descreve como usar a classe **Reflection** para obter informações sobre um assembly.

