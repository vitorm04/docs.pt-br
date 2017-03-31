---
title: "-target:winmdobj (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7581ec18db0d2741452b47ad6200482b63c102be
ms.lasthandoff: 03/13/2017

---
# <a name="targetwinmdobj-c-compiler-options"></a>/target:winmdobj (opções do compilador C#)
Se você usar a opção do compilador **/target:winmdobj**, o compilador criará um arquivo .winmdobj intermediário que pode ser convertido em um arquivo binário do Windows Runtime (.winmd). O arquivo .winmd pode, então, ser consumido por programas JavaScript e C++, bem como programas de linguagem gerenciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/target:winmdobj  
```  
  
## <a name="remarks"></a>Comentários  
 A configuração **winmdobj** indica para o compilador que um módulo intermediário é necessário. Em resposta, o Visual Studio compila a biblioteca de classes do C# como um arquivo .winmdobj. O arquivo .winmdobj pode, então, ser alimentado por meio da ferramenta de exportação <xref:Microsoft.Build.Tasks.WinMDExp> para produzir um arquivo de metadados do Windows (.winmd). O arquivo .winmd contém o código da biblioteca original e os metadados do WinMD que são usados pelo JavaScript ou C++ e pelo Windows Runtime.  
  
 A saída de um arquivo que é compilado usando a opção do compilador **/target:winmdobj** foi criada para ser usada apenas como entrada para a ferramenta de exportação WimMDExp. O arquivo .winmdobj em si não é referenciado diretamente.  
  
 A menos que você use a opção [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do primeiro arquivo de entrada. Um método [Main](../../../csharp/programming-guide/main-and-command-args/index.md) não é necessário.  
  
 Se você especificar a opção /target:winmdobj em um prompt de comando, todos os arquivos até a próxima opção **/out** ou [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) serão usados para criar o programa do Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Para definir esta opção de compilador no IDE do Visual Studio para um aplicativo da Windows Store  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.  
  
2.  Escolha a guia **Aplicativo**.  
  
3.  Na lista **Tipo de saída**, escolha **Arquivo WinMD**.  
  
     A opção **Arquivo WinMD** está disponível apenas para modelos de aplicativo [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila `filename.cs` em um arquivo .winmdobj intermediário.  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [/target (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
