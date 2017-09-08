---
title: "Como adicionar referências a bibliotecas de tipos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a0c4fc9b96ec310e20839be851cfddbb34e09201
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-add-references-to-type-libraries"></a>Como adicionar referências a bibliotecas de tipos
O Visual Studio gera um assembly de interoperabilidade que contém metadados quando você adiciona uma referência a uma biblioteca de tipos. Se um assembly de interoperabilidade primário estiver disponível, o Visual Studio usará o assembly existente antes de gerar um novo assembly de interoperabilidade.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Para adicionar uma referência a uma biblioteca de tipos no Visual Studio  
  
1.  Instale o arquivo COM DLL ou EXE em seu computador, a menos que o arquivo Windows Setup.exe execute a instalação para você.  
  
2.  Escolha **Projeto**, **Adicionar Referência**.  
  
3.  No Gerenciador de Referências, escolha **COM**.  
  
4.  Selecione a biblioteca de tipos na lista ou navegue até o arquivo .tlb.  
  
5.  Escolha **OK**.  
  
6.  No Gerenciador de Soluções, abra o menu de atalho da referência recém-adicionada e, depois, escolha **Propriedades**.  
  
7.  Na janela **Propriedades**, verifique se a propriedade **Inserir Tipos de Interoperabilidade** está definida como **True**. Isso faz com que o Visual Studio insira informações sobre tipos para tipos COM em seus executáveis, eliminando a necessidade de implantar assemblies de interoperabilidade primário com seu aplicativo.  
  
> [!NOTE]
>  As opções de menu e de caixa de diálogo podem variar, dependendo da versão do Visual Studio que você está usando.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Para adicionar uma referência a uma biblioteca de tipos para compilação da linha de comando  
  
1.  Gere um assembly de interoperabilidade, conforme descrito em [Como gerar assemblies de interoperabilidade em bibliotecas de tipos](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Use a opção do compilador [/link (Opções do Compilador do C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) com o nome do assembly de interoperabilidade para inserir informações de tipo para tipos COM nos executáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Importando uma biblioteca de tipos como um assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [Expondo componentes COM para o .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [Instruções passo a passo: Inserindo informações de tipo dos Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)   
 [Instruções passo a passo: Inserindo tipos de assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [/link (opções do compilador C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)   
 [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md)

