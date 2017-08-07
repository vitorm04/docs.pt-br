---
title: "-platform (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /platform
dev_langs:
- CSharp
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 44d4cadbc45eb141ecb7a83345d2a7a834ce5299
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="platform-c-compiler-options"></a>/platform (opções do compilador C#)
Especifica qual versão do CLR (Common Language Runtime) pode executar o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `string`  
 anycpu (padrão), anycpu32bitpreferred, ARM, x64, x86 ou Itanium.  
  
## <a name="remarks"></a>Comentários  
  
-   O **anycpu** (padrão) compila seu assembly para que ele seja executado em qualquer plataforma. Seu aplicativo será executado como um processo de 64 bits sempre que possível e realizará fallback para 32 bits quando apenas esse modo estiver disponível.  
  
-   **anycpu32bitpreferred** compila seu assembly para que ele seja executado em qualquer plataforma. Seu aplicativo é executado no modo 32 bits em sistemas que dão suporte para aplicativos de 32 bits e 64 bits. É possível especificar essa opção apenas para projetos que definem como destino o .NET Framework 4.5.  
  
-   O **ARM** compila seu assembly para que ele seja executado em um computador que tem um processador ARM (Advanced RISC Machine).  
  
-   O **x64** compila seu assembly para que ele seja executado pelo Common Language Runtime de 64 bits em um computador que dá suporte ao conjunto de instruções AMD64 e EM64T.  
  
-   O **x86** compila seu assembly para que ele seja executado pelo Common Language Runtime compatível com x86 de 32 bits.  
  
-   O **Itanium** compila seu assembly para que ele seja executado pelo Common Language Runtime de 64 bits em um computador com um processador Itanium.  
  
 Em um sistema operacional do Windows de 64 bits:  
  
-   Os assemblies compilados com **/platform:x86** são executados no CLR de 32 bits em execução no WOW64.  
  
-   Uma DLL compilada com o **/platform:anycpu** é executada no mesmo CLR que o processo no qual ela é carregada.  
  
-   Os executáveis compilados com **/platform:anycpu** são executados no CLR de 64 bits.  
  
-   Os executáveis compilados com **/platform:anycpu32bitpreferred** são executados no CLR de 32 bits.  
  
 A configuração **anycpu32bitpreferred** é válida apenas para arquivos .EXE (executáveis) e requer o .NET Framework 4.5.  
  
 Para obter mais informações sobre o desenvolvimento de um aplicativo para ser executado em um sistema operacional Windows de 64 bits, consulte [Aplicativos de 64 bits](https://msdn.microsoft.com/library/ms241064).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Modifique a propriedade **Destino da plataforma** e, para projetos que definem como destino o .NET Framework 4.5, marque ou desmarque a caixa de seleção **Preferir 32 bits**.  
  
 **Observe que /platform** não está disponível no ambiente de desenvolvimento no Visual C# Express.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a opção **/platform** para especificar que o aplicativo deve ser executado pelo CLR de 64 bits em um sistema de operacional do Windows de 64 bits.  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)

