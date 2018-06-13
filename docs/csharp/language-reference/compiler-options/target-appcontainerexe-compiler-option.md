---
title: -target:appcontainerexe (opções do compilador C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: b8765f64aeb08d816ca17fce64c13e981d85145b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216733"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (opções do compilador C#)
Se você usar a opção do compilador **-target:appcontainerexe**, o compilador criará um arquivo executável (.exe) do Windows que deverá ser executado em um contêiner de aplicativos. Essa opção é equivalente a [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), mas foi projetada para aplicativos [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Comentários  
 Para exigir que o aplicativo seja executado em um contêiner de aplicativos, esta opção define um bit no arquivo [PE](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509). Quando esse bit estiver definido, ocorrerá um erro se o método CreateProcess tentar inicializar o arquivo executável fora de um contêiner de aplicativos.  
  
 A menos que você use a opção [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../../csharp/programming-guide/main-and-command-args/index.md).  
  
 Quando você especifica essa opção em um prompt de comando, todos os arquivos até a próxima opção **-out** ou **-target** são usados para criar o arquivo executável.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Para definir esta opção do compilador no IDE  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.  
  
2.  Na guia **Aplicativo**, na lista **Tipo de saída**, escolha **Aplicativo da Windows Store**.  
  
     Essa opção está disponível apenas para modelos de aplicativo [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila `filename.cs` em um arquivo executável do Windows que pode ser executado somente em um contêiner de aplicativos.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [-target (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [-target:winexe (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
