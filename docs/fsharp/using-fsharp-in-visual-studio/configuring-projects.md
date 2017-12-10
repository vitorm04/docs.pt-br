---
title: 'Configurando projetos (F #)'
description: "Saiba como usar o Designer de projeto quando você trabalha com projetos F # no Visual Studio."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8b2ed206-34e4-4256-a6ce-0c2499561165
ms.openlocfilehash: f56fed1e16b4de1d97766f37cb1c72297d5502d5
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="configuring-projects-in-visual-studio"></a>Configurando projetos no Visual Studio

> [!NOTE]
Este artigo não é atualizado com o mais recente do Visual Studio.  Ele será atualizado.

Este tópico inclui informações sobre como usar o **Project Designer** ao trabalhar com projetos F #. Trabalhando com projetos F # não é significativamente diferente de trabalhar com projetos do Visual Basic ou c#. Geralmente, você pode usar a documentação geral de projeto do Visual Studio como sua referência principal quando você usar o F #. Este tópico fornece links para informações relevantes na documentação do Visual Studio para as configurações que são compartilhados com outras linguagens do Visual Studio e também descreve as configurações específicas para F #.

## <a name="project-designer"></a>Designer de Projeto
O **Project Designer** e o uso geral são descritos completamente no tópico [Introdução ao Project Designer](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7) na documentação do Visual Studio. O **Project Designer** consiste em várias páginas, agrupadas por funcionalidade relacionada. As páginas disponíveis para projetos F # são principalmente um subconjunto daqueles disponíveis para outros idiomas. As páginas com suporte em F # são descritas na tabela a seguir. As páginas que não estão disponíveis se relacionam aos recursos que não estão disponíveis em F #, ou que estão disponíveis apenas alterando uma opção de linha de comando. As páginas que estão disponíveis em F # lembram as páginas do c# melhor, portanto é fornecido um link para o relevantes c# **Project Designer** página.

|Página do Designer de projeto|Links relacionados|Descrição|
|---------------------|-------------|-----------|
|`Application`|[Página de aplicativo, Designer de projeto &#40; C &#35; &#41;](https://msdn.microsoft.com/library/ms247046.aspx)|Permite que você especifique configurações de nível de aplicativo e as propriedades, como se você estiver criando uma biblioteca ou um arquivo executável, qual versão do .NET Framework que o aplicativo está direcionando e obter informações sobre onde o arquivo de recursos que o aplicativo usa é armazenado.|
|`Build`|[Criar &#40; página, Designer de projeto C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Permite que você controle como o código é compilado.|
|`Build Events`|[Criar página de eventos, Designer de projeto &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Permite que você especifique comandos para execução antes ou depois de uma compilação.|
|`Debug`|[Página de Depuração, Designer de Projeto](https://msdn.microsoft.com/library/2wcdezs5.aspx)|Permite que você controle como o aplicativo é executado durante a depuração. Isso inclui o especiais modos que você deseja ativar, como SQL e de código nativo de depuração e linha de comando para uso e o que é o diretório inicial do aplicativo.|
|`Reference Paths`|[Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)|Permite que você especifique onde pesquisar para assemblies que depende do código.|

## <a name="f-specific-settings"></a>F #-configurações específicas
A tabela a seguir resume as configurações específicas para F #:

|Página do Designer de projeto|Configuração|Descrição|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|Se marcada, permite o uso de cauda instrução Microsoft intermediate language (MSIL). Isso faz com que o quadro de pilha ser reutilizado para funções de recursivas final. Equivalente a `--tailcalls` opção de compilador.|
|`Build`|`Other flags`|Permite que você especifique opções de linha de comando adicionais do compilador.|

## <a name="see-also"></a>Consulte também
 [Introdução à linguagem F # no Visual Studio](../get-started/get-started-visual-studio.md)  
 [Opções do Compilador](../language-reference/compiler-options.md)  
 [Introdução ao Designer de Projeto](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))
