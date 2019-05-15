---
title: Assemblies no Common Language Runtime
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a91890435b1c2b5b955875f52de86249c2ee79df
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607818"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Assemblies no Common Language Runtime
Assemblies são os blocos de construção de aplicativos .NET Framework; eles formam a unidade fundamental de implantação, controle de versão, reutilização, ativação de escopo e permissões de segurança. Um assembly é uma coleção de tipos e recursos compilados para funcionar juntos e formar uma unidade lógica de funcionalidade. Um assembly oferece ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo. Para o tempo de execução, um tipo não existe fora do contexto de um assembly.  
  
 Um assembly executa as seguintes funções:  
  
- Ele contém código que o Common Language Runtime executa. O código MSIL (Microsoft Intermediate Language), em um arquivo PE (Portable Executable), não será executado se não tiver um manifesto de assembly associado. Observe que cada assembly pode ter somente um ponto de entrada (ou seja, `DllMain`, `WinMain` ou `Main`).  
  
- Ele forma um limite de segurança. Um assembly é a unidade na qual as permissões são solicitadas e concedidas. Para saber mais sobre limites de segurança e como eles se aplicam a assemblies, confira [Assembly Security Considerations](../../../docs/framework/app-domains/assembly-security-considerations.md) (Considerações sobre segurança do assembly).  
  
- Ele forma um limite de tipo. A identidade de cada tipo inclui o nome do assembly no qual ele reside. Um tipo chamado `MyType`, carregado no escopo de um assembly, não é o mesmo de um tipo chamado `MyType`, carregado no escopo de outro assembly.  
  
- Ele forma um limite de escopo de referência. O manifesto do assembly contém metadados do assembly usados para resolver tipos e atender a solicitações de recurso. Ele especifica os tipos e os recursos expostos fora do assembly. O manifesto também enumera outros assemblies dos quais ele depende.  
  
- Ele forma um limite de versão. O assembly é a menor unidade com controle de versão do Common Language Runtime; todos os tipos e recursos no mesmo assembly têm uma versão como uma unidade. O manifesto do assembly descreve as dependências de versão que você especifica para qualquer assembly dependente. Para saber mais sobre o controle de versão, confira [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md) (Controle de versão do assembly).  
  
- Ele forma uma unidade de implantação. Quando um aplicativo é iniciado, somente os assemblies que o aplicativo chama inicialmente devem estar presentes. Outros assemblies, como recursos de localização ou assemblies contendo classes de utilitário, podem ser recuperados sob demanda. Isso permite que aplicativos sejam mantidos simples e finos quando baixados pela primeira vez. Para saber mais sobre como implantar assemblies, confira [Implantando aplicativos](../../../docs/framework/deployment/index.md).  
  
- Essa é a unidade na qual a execução lado a lado é compatível. Para saber mais sobre como executar várias versões de um assembly, confira [Assemblies and Side-by-Side Execution](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md) (Assemblies e execução lado a lado).  
  
 Assemblies podem ser estáticos ou dinâmicos. Assemblies estáticos podem incluir tipos do .NET Framework (interfaces e classes), bem como recursos para o assembly (bitmaps, arquivos JPEG, arquivos de recurso etc.). Assemblies estáticos são armazenados em disco em arquivos PE. Você também pode usar o .NET Framework para criar assemblies dinâmicos, executados diretamente da memória e não são salvos em disco antes da execução. Você pode salvar assemblies dinâmicos em disco após sua execução.  
  
 Existem várias maneiras de criar assemblies. É possível usar ferramentas de desenvolvimento, como Visual Studio, que você utilizava anteriormente para criar arquivos .dll ou .exe. Você pode usar ferramentas fornecidas pelo [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] para criar assemblies com módulos criados em outros ambientes de desenvolvimento. Você também pode usar APIs do Common Language Runtime, como <xref:System.Reflection.Emit?displayProperty=nameWithType>, a fim de criar assemblies dinâmicos.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Conteúdo do assembly](../../../docs/framework/app-domains/assembly-contents.md)|Descreve os elementos que compõem um assembly.|  
|[Manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md)|Descreve os dados no manifesto do assembly e como ele são armazenados em assemblies.|  
|[Cache de assembly global](../../../docs/framework/app-domains/gac.md)|Descreve o cache de assembly global e como ele é usado com assemblies.|  
|[Assemblies de nomes fortes](../../../docs/framework/app-domains/strong-named-assemblies.md)|Descreve as características de assemblies de nome forte.|  
|[Considerações sobre segurança de assembly](../../../docs/framework/app-domains/assembly-security-considerations.md)|Discute como a segurança funciona com assemblies.|  
|[Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md)|Apresenta uma visão geral sobre a política de controle de versão do .NET Framework.|  
|[Posicionamento do assembly](../../../docs/framework/app-domains/assembly-placement.md)|Discute onde localizar assemblies.|  
|[Assemblies e execução lado a lado](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Fornece uma visão geral do uso de várias versões do tempo de execução ou de um assembly simultaneamente.|  
|[Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)|Descreve como criar, assinar e definir atributos em assemblies.|  
|[Emissão de métodos e assemblies dinâmicos](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Descreve como criar assemblies dinâmicos.|  
|[Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Descreve como o .NET Framework resolve referências de assembly em tempo de execução.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
