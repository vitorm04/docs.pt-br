---
title: 'Como: Adicionar referências a bibliotecas de tipos'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3fda2af84ff74e129c36dc966bad247bdf9e20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427130"
---
# <a name="how-to-add-references-to-type-libraries"></a>Como: Adicionar referências a bibliotecas de tipos
O Visual Studio gera um assembly de interoperabilidade que contém metadados quando você adiciona uma referência a uma biblioteca de tipos. Se um assembly de interoperabilidade primário estiver disponível, o Visual Studio usará o assembly existente antes de gerar um novo assembly de interoperabilidade.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Para adicionar uma referência a uma biblioteca de tipos no Visual Studio  
  
1. Instale o arquivo COM DLL ou EXE em seu computador, a menos que o arquivo Windows Setup.exe execute a instalação para você.  
  
2. Escolha **Projeto**, **Adicionar Referência**.  
  
3. No Gerenciador de Referências, escolha **COM**.  
  
4. Selecione a biblioteca de tipos na lista ou navegue até o arquivo .tlb.  
  
5. Escolha **OK**.  
  
6. No Gerenciador de Soluções, abra o menu de atalho da referência recém-adicionada e, depois, escolha **Propriedades**.  
  
7. Na janela **Propriedades**, verifique se a propriedade **Inserir Tipos de Interoperabilidade** está definida como **True**. Isso faz com que o Visual Studio insira informações sobre tipos para tipos COM em seus executáveis, eliminando a necessidade de implantar assemblies de interoperabilidade primário com seu aplicativo.  
  
> [!NOTE]
>  As opções de menu e de caixa de diálogo podem variar, dependendo da versão do Visual Studio que você está usando.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Para adicionar uma referência a uma biblioteca de tipos para compilação da linha de comando  
  
1. Gere um assembly de interoperabilidade, conforme descrito em [Como: Gerar assemblies de interoperabilidade com base em bibliotecas de tipos](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2. Use a opção do compilador [/link (Opções do Compilador do C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) com o nome do assembly de interoperabilidade para inserir informações de tipo para tipos COM nos executáveis.  
  
## <a name="see-also"></a>Consulte também

- [Importando uma biblioteca de tipos como um assembly](importing-a-type-library-as-an-assembly.md)
- [Expondo componentes do COM ao .NET Framework](exposing-com-components.md)
- [Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [Passo a passo: Inserindo tipos de assemblies gerenciados no Visual Studio (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/link (opções do compilador C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
