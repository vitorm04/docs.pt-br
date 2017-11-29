---
title: "-warnaserror (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28c2cdc26d32d98e617a0c4b8cd282d2fbc87f4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-c-compiler-options"></a>/warnaserror (opções do compilador C#)
A opção **/warnaserror+** trata todos os avisos como erros  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a>Comentários  
 Quaisquer mensagens que seriam, normalmente, ser relatadas como avisos, são relatadas como erros e o processo de build é interrompido (os arquivos de saída não são compilados).  
  
 Por padrão, a opção **/warnaserror-** está em vigor, o que faz com que os avisos não impeçam a geração de um arquivo de saída. A **/warnaserror**, que é a mesma que **/warnaserror+**, faz com que os avisos sejam tratados como erros.  
  
 Opcionalmente, se você deseja que apenas avisos específicos sejam tratados como erros, você pode especificar uma lista separada por vírgulas de números de aviso para serem tratados como erros.  
  
 Use [/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) para especificar o nível de avisos que você deseja que o compilador exiba. Use [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) para desabilitar determinados avisos.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Modifique a propriedade **Tratar Avisos como Erros**.  
  
     Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.  
  
## <a name="example"></a>Exemplo  
 Compilar `in.cs` e fazer com que o compilador não exiba avisos:  
  
```console  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
