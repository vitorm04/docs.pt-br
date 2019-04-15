---
title: 'Como: Determinar o nome totalmente qualificado de um assembly'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a4ef1f5bde121d5773925437307b2749aa7282
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097521"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a>Como: Determinar o nome totalmente qualificado de um assembly
Para descobrir o nome totalmente qualificado de um assembly no cache de assembly global, use a Ferramenta Cache de Assembly Global ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Confira [Como Exibir o conteúdo do cache de assembly global](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Para assemblies que não estão no cache de assembly global, você pode obter o nome totalmente qualificado do assembly de várias maneiras: pode usar código para produzir a saída de informações para o console ou para uma variável ou pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contêm o nome totalmente qualificado.  
  
-   Se o assembly já estiver carregado pelo aplicativo, você poderá recuperar o valor da propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado. Você pode usar essa abordagem se o assembly estiver ou não no GAC. O exemplo fornece uma ilustração.  
  
-   Se você souber o caminho do sistema de arquivos do assembly, poderá chamar o método (`Shared` no Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> estático para obter o nome totalmente qualificado do assembly. Este é um exemplo simples.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Você pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contêm o nome totalmente qualificado.  
  
 Para obter mais informações sobre atributos de assembly de configuração, como a versão, a cultura e o nome do assembly, consulte [Definindo atributos do assembly](../../../docs/framework/app-domains/set-assembly-attributes.md). Para obter mais informações sobre como atribuir um nome forte a um assembly, consulte [Criando e usando assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como exibir o nome totalmente qualificado de um assembly que contém uma classe especificada no console. Como ele recupera o nome de um assembly que o aplicativo já carregou, não importa se o assembly está no GAC.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Nomes de assembly](../../../docs/framework/app-domains/assembly-names.md)
- [Criando assemblies](../../../docs/framework/app-domains/create-assemblies.md)
- [Criando e usando assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Cache de assemblies global](../../../docs/framework/app-domains/gac.md)
- [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
