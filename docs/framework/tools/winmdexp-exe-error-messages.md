---
title: Mensagens de erro do winmdexp.exe
ms.date: 03/30/2017
f1_keywords:
- WME1095
- WME1110
- WME15
- WME1094
- WME1078
- WME1080
- WME1014
- WME1025
- WME1089
- WME1111
- WME1010
- WME1013
- WME1055
- WME1005
- WME1033
- WME1003
- WME1011
- WME1046
- WME0013
- WME1032
- WME1029
- WME1048
- WME1019
- WME1106
- WME0012
- WME1017
- WME1098
- WME1039
- WME20
- WME1006
- WME1088
- WME0004
- WME10
- WME12
- WME0015
- WME0017
- WME1026
- WME1045
- WME1002
- WME1051
- WME1107
- WME1100
- WME1072
- WME1090
- WME1105
- WME1022
- WME11
- WME17
- WME1063
- WME1041
- WME1057
- WME1037
- WME1007
- WME3
- WME1096
- WME0003
- WME0006
- WME1065
- WME1102
- WME1070
- WME1113
- WME1064
- WME1061
- WME1066
- WME1018
- WME1049
- WME1027
- WME1101
- WME1058
- WME0005
- WME1083
- WME1004
- WME1073
- WME1087
- WME1077
- WME19
- WME1086
- WME1085
- WME1040
- WME8
- WME1081
- WME1023
- WME4
- WME1050
- WME7
- WME1091
- WME14
- WME0007
- WME1024
- WME1012
- WME1036
- WME0010
- WME1104
- WME1035
- WME1021
- WME1075
- WME5
- WME13
- WME1074
- WME1028
- WME0014
- WME1030
- WME1008
- WME1052
- WME1079
- WME1054
- WME1093
- WME1042
- WME2
- WME1062
- WME6
- WME1001
- WME0011
- WME16
- WME0001
- WME1020
- WME1084
- WME1103
- WME1092
- WME1
- WME0002
- WME1112
- WME1016
- WME1060
- WME0008
- WME0016
- WME1097
- WME1034
- WME1108
- WME1082
- WME1099
- WME1069
- WME1031
- WME1009
- WME1068
- WME1067
- WME1059
- WME18
- WME1038
- WME0009
- WME1109
- WME1056
- WME1076
- WME1071
- WME1044
- WME1043
- WME1053
- WME1015
- WME1047
- WME9
helpviewer_keywords:
- Winmdexp.exe, error messages
- Windows Runtime Metadata Export Tool, error messages
- error messages, Winmdexp.exe
ms.assetid: 8271973c-deba-47a6-8e5e-04ce63f146ad
ms.openlocfilehash: 5d75f60cb96ddb7bd9e24a7cdc4b8d2b61aff8f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104182"
---
# <a name="winmdexpexe-error-messages"></a><span data-ttu-id="e9cd2-102">Mensagens de erro do winmdexp.exe</span><span class="sxs-lookup"><span data-stu-id="e9cd2-102">Winmdexp.exe Error Messages</span></span>
<span data-ttu-id="e9cd2-103">O processo de compilação chama [Winmdexp.exe (Ferramenta de Exportação de Metadados do Windows Runtime)](winmdexp-exe-windows-runtime-metadata-export-tool.md) quando você usa o modelo **Componente do Tempo de Execução do Windows** no Visual Studio 2012, portanto, as mensagens de erro de Winmdexp.exe aparecem na **Lista de Erros**.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-103">The build process calls [Winmdexp.exe (Windows Runtime Metadata Export Tool)](winmdexp-exe-windows-runtime-metadata-export-tool.md) when you use the **Windows Runtime Component** template in Visual Studio 2012, so Winmdexp.exe error messages appear in the **Error List**.</span></span> <span data-ttu-id="e9cd2-104">O Winmdexp.exe opera em um módulo compilado com a opção `/target:winmdobj`.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-104">Winmdexp.exe operates on a module that is compiled with the `/target:winmdobj` option.</span></span> <span data-ttu-id="e9cd2-105">Como ele requer um módulo compilado como entrada, suas mensagens de erro não aparecerão se a compilação for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-105">Because it requires a compiled module as input, its error messages don't appear unless compilation succeeds.</span></span>  
  
 <span data-ttu-id="e9cd2-106">As mensagens de erro foram projetadas para conter todas as informações necessárias para resolver as condições de erro relatadas.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-106">The error messages are designed to contain all the information you need to address the error conditions they report.</span></span> <span data-ttu-id="e9cd2-107">No entanto, alguns problemas exigem mais informações do que a mensagem pode conter.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-107">However, some problems require more information than will fit in the message.</span></span> <span data-ttu-id="e9cd2-108">Encontre informações adicionais em [Diagnosticando condições de erro do componente do Tempo de Execução do Windows](https://go.microsoft.com/fwlink/p/?LinkId=251127) no Centro de Desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-108">You can find additional information in [Diagnosing Windows Runtime component error conditions](https://go.microsoft.com/fwlink/p/?LinkId=251127) in the Windows Dev Center.</span></span>  
  
 <span data-ttu-id="e9cd2-109">Se o erro não for abordado neste artigo e você achar que a mensagem não contém informações suficientes para resolver o problema, use o link de comentários nesse artigo e inclua a mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="e9cd2-109">If your error is not discussed in that article, and you feel that the message doesn't contain sufficient information to address the issue, please use the feedback link in that article and include the error message.</span></span> <span data-ttu-id="e9cd2-110">Outra opção é registrar um bug no [Site do Microsoft Connect](https://go.microsoft.com/fwlink/p/?LinkId=251130).</span><span class="sxs-lookup"><span data-stu-id="e9cd2-110">Alternatively, you can file a bug at the [Microsoft Connect website](https://go.microsoft.com/fwlink/p/?LinkId=251130).</span></span> <span data-ttu-id="e9cd2-111">Você também pode procurar mais informações nos [Fóruns da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=251129).</span><span class="sxs-lookup"><span data-stu-id="e9cd2-111">You can also look for more information on the [Microsoft Forums](https://go.microsoft.com/fwlink/p/?LinkId=251129).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cd2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9cd2-112">See also</span></span>

- [<span data-ttu-id="e9cd2-113">Winmdexp.exe (Ferramenta de Exportação de Metadados do Tempo de Execução do Windows)</span><span class="sxs-lookup"><span data-stu-id="e9cd2-113">Winmdexp.exe (Windows Runtime Metadata Export Tool)</span></span>](winmdexp-exe-windows-runtime-metadata-export-tool.md)
- [<span data-ttu-id="e9cd2-114">Diagnosticando condições de erro do componente do Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="e9cd2-114">Diagnosing Windows Runtime component error conditions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=251127)
