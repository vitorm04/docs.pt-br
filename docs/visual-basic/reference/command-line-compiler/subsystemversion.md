---
title: "-subsystemversion (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Opção de compilador /subsystemversion [Visual Basic]"
  - "Opção de compilador -subsystemversion [Visual Basic]"
  - "Opção de compilador subsystemversion [Visual Basic]"
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /subsystemversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica a versão mínima do subsistema no qual pode executar o arquivo executável gerado, assim, determinar as versões do Windows no qual o arquivo executável pode executar. Normalmente, essa opção garante que o arquivo executável pode aproveitar os recursos de segurança em especial que não estão disponíveis com versões anteriores do Windows.  
  
> [!NOTE]
>  Para especificar o próprio subsistema, use o [/destino](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opção de compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `major.minor`  
 A versão mínima necessária do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias. Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional que é mais antigo que o Windows 7 se você definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico. Você deve especificar os valores de `major` e `minor` como inteiros.  
  
 Zeros à esquerda `minor` versão não altera a versão, mas fazer zeros à direita. Por exemplo, 6.1 e 6.01 referem-se a mesma versão, mas 6.10 refere-se a uma versão diferente. É recomendável expressar a versão secundária como dois dígitos para evitar confusão.  
  
## <a name="remarks"></a>Comentários  
 A seguinte tabela lista as versões do subsistema comuns do Windows.  
  
|Versão do Windows|Versão do subsistema|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|6.02|  
  
## <a name="default-values"></a>Valores padrão  
 O valor padrão de **/subsystemversion** opção de compilador depende das condições na lista a seguir:  
  
-   O valor padrão é 6.02 se qualquer opção de compilador na lista a seguir é definida:  
  
    -   [/target: appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [/target: winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [/Platform:ARM](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   O valor padrão é 6.00 se você estiver usando o MSBuild, você deseja [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], e você não definir qualquer uma das opções de compilador que foram especificadas anteriormente na lista.  
  
-   O valor padrão é 4.00 se nenhuma das condições anteriores for true.  
  
## <a name="setting-this-option"></a>Definindo esta opção  
 Para definir o **/subsystemversion** opção de compilador no Visual Studio, abra o arquivo. vbproj e especifique um valor para o `SubsystemVersion` propriedade no XML MSBuild. Você não pode definir essa opção no IDE do Visual Studio. Para obter mais informações, consulte "Valores padrão" anteriormente neste tópico ou [Propriedades comuns de projeto MSBuild](/visual-studio/msbuild/common-msbuild-project-properties).  
  

  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
 [Propriedades MSBuild](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/ee3538c5-0d7d-4c18-a1d7-edf460cd1c8a/locales/en-US)