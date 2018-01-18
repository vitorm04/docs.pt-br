---
title: "Coleções de esquema ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="e3bbd-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="e3bbd-102">ODBC Schema Collections</span></span>
<span data-ttu-id="e3bbd-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="e3bbd-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="e3bbd-104">Microsoft SQL Server ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="e3bbd-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="e3bbd-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="e3bbd-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e3bbd-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-106">Tables</span></span>  
  
-   <span data-ttu-id="e3bbd-107">Índices</span><span class="sxs-lookup"><span data-stu-id="e3bbd-107">Indexes</span></span>  
  
-   <span data-ttu-id="e3bbd-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-108">Columns</span></span>  
  
-   <span data-ttu-id="e3bbd-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e3bbd-109">Procedures</span></span>  
  
-   <span data-ttu-id="e3bbd-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3bbd-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e3bbd-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3bbd-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e3bbd-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="e3bbd-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="e3bbd-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="e3bbd-113">Tables and Views</span></span>  
  
|<span data-ttu-id="e3bbd-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-114">ColumnName</span></span>|<span data-ttu-id="e3bbd-115">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-116">TABLE_CAT</span></span>|<span data-ttu-id="e3bbd-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-117">String</span></span>|  
|<span data-ttu-id="e3bbd-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-118">TABLE_SCHEM</span></span>|<span data-ttu-id="e3bbd-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-119">String</span></span>|  
|<span data-ttu-id="e3bbd-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-120">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-121">String</span></span>|  
|<span data-ttu-id="e3bbd-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-122">TABLE_TYPE</span></span>|<span data-ttu-id="e3bbd-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-123">String</span></span>|  
|<span data-ttu-id="e3bbd-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-124">REMARKS</span></span>|<span data-ttu-id="e3bbd-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e3bbd-126">Índices</span><span class="sxs-lookup"><span data-stu-id="e3bbd-126">Indexes</span></span>  
  
|<span data-ttu-id="e3bbd-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-127">ColumnName</span></span>|<span data-ttu-id="e3bbd-128">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-129">TABLE_CAT</span></span>|<span data-ttu-id="e3bbd-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-130">String</span></span>|  
|<span data-ttu-id="e3bbd-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-131">TABLE_SCHEM</span></span>|<span data-ttu-id="e3bbd-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-132">String</span></span>|  
|<span data-ttu-id="e3bbd-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-133">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-134">String</span></span>|  
|<span data-ttu-id="e3bbd-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-135">NON_UNIQUE</span></span>|<span data-ttu-id="e3bbd-136">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-136">Int16</span></span>|  
|<span data-ttu-id="e3bbd-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-138">String</span></span>|  
|<span data-ttu-id="e3bbd-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-139">INDEX_NAME</span></span>|<span data-ttu-id="e3bbd-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-140">String</span></span>|  
|<span data-ttu-id="e3bbd-141">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-141">TYPE</span></span>|<span data-ttu-id="e3bbd-142">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-142">Int16</span></span>|  
|<span data-ttu-id="e3bbd-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-144">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-144">Int16</span></span>|  
|<span data-ttu-id="e3bbd-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-145">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-146">String</span></span>|  
|<span data-ttu-id="e3bbd-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="e3bbd-147">ASC_OR_DESC</span></span>|<span data-ttu-id="e3bbd-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-148">String</span></span>|  
|<span data-ttu-id="e3bbd-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-149">CARDINATLITY</span></span>|<span data-ttu-id="e3bbd-150">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-150">Int32</span></span>|  
|<span data-ttu-id="e3bbd-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-151">PAGES</span></span>|<span data-ttu-id="e3bbd-152">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-152">Int32</span></span>|  
|<span data-ttu-id="e3bbd-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-153">FILTER_CONDITION</span></span>|<span data-ttu-id="e3bbd-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-154">String</span></span>|  
|<span data-ttu-id="e3bbd-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e3bbd-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-156">String</span></span>|  
|<span data-ttu-id="e3bbd-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-158">Byte</span><span class="sxs-lookup"><span data-stu-id="e3bbd-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e3bbd-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-159">Columns</span></span>  
  
|<span data-ttu-id="e3bbd-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-160">ColumnName</span></span>|<span data-ttu-id="e3bbd-161">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-162">TABLE_CAT</span></span>|<span data-ttu-id="e3bbd-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-163">String</span></span>|  
|<span data-ttu-id="e3bbd-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-164">TABLE_SCHEM</span></span>|<span data-ttu-id="e3bbd-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-165">String</span></span>|  
|<span data-ttu-id="e3bbd-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-166">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-167">String</span></span>|  
|<span data-ttu-id="e3bbd-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-168">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-169">String</span></span>|  
|<span data-ttu-id="e3bbd-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-170">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-171">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-171">Int16</span></span>|  
|<span data-ttu-id="e3bbd-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-172">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-173">String</span></span>|  
|<span data-ttu-id="e3bbd-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-174">COLUMN_SIZE</span></span>|<span data-ttu-id="e3bbd-175">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-175">Int32</span></span>|  
|<span data-ttu-id="e3bbd-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="e3bbd-177">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-177">Int32</span></span>|  
|<span data-ttu-id="e3bbd-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e3bbd-179">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-179">Int16</span></span>|  
|<span data-ttu-id="e3bbd-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e3bbd-181">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-181">Int16</span></span>|  
|<span data-ttu-id="e3bbd-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-182">NULLABLE</span></span>|<span data-ttu-id="e3bbd-183">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-183">Int16</span></span>|  
|<span data-ttu-id="e3bbd-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-184">REMARKS</span></span>|<span data-ttu-id="e3bbd-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-185">String</span></span>|  
|<span data-ttu-id="e3bbd-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e3bbd-186">COLUMN_DEF</span></span>|<span data-ttu-id="e3bbd-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-187">String</span></span>|  
|<span data-ttu-id="e3bbd-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-189">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-189">Int16</span></span>|  
|<span data-ttu-id="e3bbd-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e3bbd-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e3bbd-191">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-191">Int16</span></span>|  
|<span data-ttu-id="e3bbd-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e3bbd-193">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-193">Int32</span></span>|  
|<span data-ttu-id="e3bbd-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-195">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-195">Int32</span></span>|  
|<span data-ttu-id="e3bbd-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-196">IS_NULLABLE</span></span>|<span data-ttu-id="e3bbd-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-197">String</span></span>|  
|<span data-ttu-id="e3bbd-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3bbd-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e3bbd-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-199">String</span></span>|  
|<span data-ttu-id="e3bbd-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e3bbd-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-201">String</span></span>|  
|<span data-ttu-id="e3bbd-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-203">Byte</span><span class="sxs-lookup"><span data-stu-id="e3bbd-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e3bbd-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e3bbd-204">Procedures</span></span>  
  
|<span data-ttu-id="e3bbd-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-205">ColumnName</span></span>|<span data-ttu-id="e3bbd-206">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="e3bbd-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-208">String</span></span>|  
|<span data-ttu-id="e3bbd-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e3bbd-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-210">String</span></span>|  
|<span data-ttu-id="e3bbd-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-212">String</span></span>|  
|<span data-ttu-id="e3bbd-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e3bbd-214">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-214">Int32</span></span>|  
|<span data-ttu-id="e3bbd-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e3bbd-216">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-216">Int32</span></span>|  
|<span data-ttu-id="e3bbd-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e3bbd-218">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-218">Int32</span></span>|  
|<span data-ttu-id="e3bbd-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-219">REMARKS</span></span>|<span data-ttu-id="e3bbd-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-220">String</span></span>|  
|<span data-ttu-id="e3bbd-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e3bbd-222">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e3bbd-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3bbd-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e3bbd-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-224">ColumnName</span></span>|<span data-ttu-id="e3bbd-225">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="e3bbd-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-227">String</span></span>|  
|<span data-ttu-id="e3bbd-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e3bbd-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-229">String</span></span>|  
|<span data-ttu-id="e3bbd-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-231">String</span></span>|  
|<span data-ttu-id="e3bbd-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-232">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-233">String</span></span>|  
|<span data-ttu-id="e3bbd-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-234">COLUMN_TYPE</span></span>|<span data-ttu-id="e3bbd-235">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-235">Int16</span></span>|  
|<span data-ttu-id="e3bbd-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-236">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-237">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-237">Int16</span></span>|  
|<span data-ttu-id="e3bbd-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-238">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-239">String</span></span>|  
|<span data-ttu-id="e3bbd-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-240">COLUMN_SIZE</span></span>|<span data-ttu-id="e3bbd-241">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-241">Int32</span></span>|  
|<span data-ttu-id="e3bbd-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="e3bbd-243">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-243">Int32</span></span>|  
|<span data-ttu-id="e3bbd-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e3bbd-245">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-245">Int16</span></span>|  
|<span data-ttu-id="e3bbd-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e3bbd-247">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-247">Int16</span></span>|  
|<span data-ttu-id="e3bbd-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-248">NULLABLE</span></span>|<span data-ttu-id="e3bbd-249">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-249">Int16</span></span>|  
|<span data-ttu-id="e3bbd-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-250">REMARKS</span></span>|<span data-ttu-id="e3bbd-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-251">String</span></span>|  
|<span data-ttu-id="e3bbd-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e3bbd-252">COLUMN_DEF</span></span>|<span data-ttu-id="e3bbd-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-253">String</span></span>|  
|<span data-ttu-id="e3bbd-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-255">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-255">Int16</span></span>|  
|<span data-ttu-id="e3bbd-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e3bbd-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e3bbd-257">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-257">Int16</span></span>|  
|<span data-ttu-id="e3bbd-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e3bbd-259">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-259">Int32</span></span>|  
|<span data-ttu-id="e3bbd-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-261">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-261">Int32</span></span>|  
|<span data-ttu-id="e3bbd-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-262">IS_NULLABLE</span></span>|<span data-ttu-id="e3bbd-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-263">String</span></span>|  
|<span data-ttu-id="e3bbd-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3bbd-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e3bbd-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-265">String</span></span>|  
|<span data-ttu-id="e3bbd-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e3bbd-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-267">String</span></span>|  
|<span data-ttu-id="e3bbd-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-269">Byte</span><span class="sxs-lookup"><span data-stu-id="e3bbd-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e3bbd-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3bbd-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e3bbd-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-271">ColumnName</span></span>|<span data-ttu-id="e3bbd-272">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="e3bbd-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-274">String</span></span>|  
|<span data-ttu-id="e3bbd-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e3bbd-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-276">String</span></span>|  
|<span data-ttu-id="e3bbd-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-278">String</span></span>|  
|<span data-ttu-id="e3bbd-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-279">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-280">String</span></span>|  
|<span data-ttu-id="e3bbd-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-281">COLUMN_TYPE</span></span>|<span data-ttu-id="e3bbd-282">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-282">Int16</span></span>|  
|<span data-ttu-id="e3bbd-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-283">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-284">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-284">Int16</span></span>|  
|<span data-ttu-id="e3bbd-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-285">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-286">String</span></span>|  
|<span data-ttu-id="e3bbd-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-287">COLUMN_SIZE</span></span>|<span data-ttu-id="e3bbd-288">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-288">Int32</span></span>|  
|<span data-ttu-id="e3bbd-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="e3bbd-290">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-290">Int32</span></span>|  
|<span data-ttu-id="e3bbd-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e3bbd-292">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-292">Int16</span></span>|  
|<span data-ttu-id="e3bbd-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e3bbd-294">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-294">Int16</span></span>|  
|<span data-ttu-id="e3bbd-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-295">NULLABLE</span></span>|<span data-ttu-id="e3bbd-296">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-296">Int16</span></span>|  
|<span data-ttu-id="e3bbd-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-297">REMARKS</span></span>|<span data-ttu-id="e3bbd-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-298">String</span></span>|  
|<span data-ttu-id="e3bbd-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e3bbd-299">COLUMN_DEF</span></span>|<span data-ttu-id="e3bbd-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-300">String</span></span>|  
|<span data-ttu-id="e3bbd-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-302">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-302">Int16</span></span>|  
|<span data-ttu-id="e3bbd-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e3bbd-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e3bbd-304">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-304">Int16</span></span>|  
|<span data-ttu-id="e3bbd-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e3bbd-306">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-306">Int32</span></span>|  
|<span data-ttu-id="e3bbd-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-308">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-308">Int32</span></span>|  
|<span data-ttu-id="e3bbd-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-309">IS_NULLABLE</span></span>|<span data-ttu-id="e3bbd-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-310">String</span></span>|  
|<span data-ttu-id="e3bbd-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3bbd-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e3bbd-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-312">String</span></span>|  
|<span data-ttu-id="e3bbd-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e3bbd-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-314">String</span></span>|  
|<span data-ttu-id="e3bbd-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-316">Byte</span><span class="sxs-lookup"><span data-stu-id="e3bbd-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="e3bbd-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="e3bbd-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="e3bbd-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="e3bbd-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e3bbd-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-319">Tables</span></span>  
  
-   <span data-ttu-id="e3bbd-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-320">Columns</span></span>  
  
-   <span data-ttu-id="e3bbd-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e3bbd-321">Procedures</span></span>  
  
-   <span data-ttu-id="e3bbd-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3bbd-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e3bbd-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3bbd-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e3bbd-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="e3bbd-324">Views</span></span>  
  
-   <span data-ttu-id="e3bbd-325">Índices</span><span class="sxs-lookup"><span data-stu-id="e3bbd-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="e3bbd-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="e3bbd-326">Tables and Views</span></span>  
  
|<span data-ttu-id="e3bbd-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-327">ColumnName</span></span>|<span data-ttu-id="e3bbd-328">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-330">String</span></span>|  
|<span data-ttu-id="e3bbd-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-331">TABLE_OWNER</span></span>|<span data-ttu-id="e3bbd-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-332">String</span></span>|  
|<span data-ttu-id="e3bbd-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-333">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-334">String</span></span>|  
|<span data-ttu-id="e3bbd-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-335">TABLE_TYPE</span></span>|<span data-ttu-id="e3bbd-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-336">String</span></span>|  
|<span data-ttu-id="e3bbd-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-337">REMARKS</span></span>|<span data-ttu-id="e3bbd-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e3bbd-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-339">Columns</span></span>  
  
|<span data-ttu-id="e3bbd-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-340">ColumnName</span></span>|<span data-ttu-id="e3bbd-341">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-343">String</span></span>|  
|<span data-ttu-id="e3bbd-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-344">TABLE_OWNER</span></span>|<span data-ttu-id="e3bbd-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-345">String</span></span>|  
|<span data-ttu-id="e3bbd-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-346">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-347">String</span></span>|  
|<span data-ttu-id="e3bbd-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-348">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-349">String</span></span>|  
|<span data-ttu-id="e3bbd-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-350">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-351">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-351">Int16</span></span>|  
|<span data-ttu-id="e3bbd-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-352">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-353">String</span></span>|  
|<span data-ttu-id="e3bbd-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-354">PRECISION</span></span>|<span data-ttu-id="e3bbd-355">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-355">Int32</span></span>|  
|<span data-ttu-id="e3bbd-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-356">LENGTH</span></span>|<span data-ttu-id="e3bbd-357">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-357">Int32</span></span>|  
|<span data-ttu-id="e3bbd-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-358">SCALE</span></span>|<span data-ttu-id="e3bbd-359">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-359">Int16</span></span>|  
|<span data-ttu-id="e3bbd-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-360">RADIX</span></span>|<span data-ttu-id="e3bbd-361">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-361">Int16</span></span>|  
|<span data-ttu-id="e3bbd-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-362">NULLABLE</span></span>|<span data-ttu-id="e3bbd-363">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-363">Int16</span></span>|  
|<span data-ttu-id="e3bbd-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-364">REMARKS</span></span>|<span data-ttu-id="e3bbd-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-365">String</span></span>|  
|<span data-ttu-id="e3bbd-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-367">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e3bbd-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e3bbd-368">Procedures</span></span>  
  
|<span data-ttu-id="e3bbd-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-369">ColumnName</span></span>|<span data-ttu-id="e3bbd-370">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-372">String</span></span>|  
|<span data-ttu-id="e3bbd-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e3bbd-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-374">String</span></span>|  
|<span data-ttu-id="e3bbd-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-376">String</span></span>|  
|<span data-ttu-id="e3bbd-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e3bbd-378">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-378">Int16</span></span>|  
|<span data-ttu-id="e3bbd-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e3bbd-380">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-380">Int16</span></span>|  
|<span data-ttu-id="e3bbd-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e3bbd-382">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-382">Int16</span></span>|  
|<span data-ttu-id="e3bbd-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-383">REMARKS</span></span>|<span data-ttu-id="e3bbd-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-384">String</span></span>|  
|<span data-ttu-id="e3bbd-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e3bbd-386">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e3bbd-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3bbd-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e3bbd-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-388">ColumnName</span></span>|<span data-ttu-id="e3bbd-389">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-391">String</span></span>|  
|<span data-ttu-id="e3bbd-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e3bbd-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-393">String</span></span>|  
|<span data-ttu-id="e3bbd-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-395">String</span></span>|  
|<span data-ttu-id="e3bbd-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-396">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-397">String</span></span>|  
|<span data-ttu-id="e3bbd-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-398">COLUMN_TYPE</span></span>|<span data-ttu-id="e3bbd-399">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-399">Int16</span></span>|  
|<span data-ttu-id="e3bbd-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-400">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-401">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-401">Int16</span></span>|  
|<span data-ttu-id="e3bbd-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-402">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-403">String</span></span>|  
|<span data-ttu-id="e3bbd-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-404">PRECISION</span></span>|<span data-ttu-id="e3bbd-405">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-405">Int32</span></span>|  
|<span data-ttu-id="e3bbd-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-406">LENGTH</span></span>|<span data-ttu-id="e3bbd-407">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-407">Int32</span></span>|  
|<span data-ttu-id="e3bbd-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-408">SCALE</span></span>|<span data-ttu-id="e3bbd-409">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-409">Int16</span></span>|  
|<span data-ttu-id="e3bbd-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-410">RADIX</span></span>|<span data-ttu-id="e3bbd-411">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-411">Int16</span></span>|  
|<span data-ttu-id="e3bbd-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-412">NULLABLE</span></span>|<span data-ttu-id="e3bbd-413">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-413">Int16</span></span>|  
|<span data-ttu-id="e3bbd-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-414">REMARKS</span></span>|<span data-ttu-id="e3bbd-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-415">String</span></span>|  
|<span data-ttu-id="e3bbd-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="e3bbd-416">OVERLOAD</span></span>|<span data-ttu-id="e3bbd-417">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-417">Int32</span></span>|  
|<span data-ttu-id="e3bbd-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-419">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="e3bbd-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="e3bbd-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="e3bbd-421">O Driver de ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="e3bbd-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e3bbd-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-422">Tables</span></span>  
  
-   <span data-ttu-id="e3bbd-423">Índices</span><span class="sxs-lookup"><span data-stu-id="e3bbd-423">Indexes</span></span>  
  
-   <span data-ttu-id="e3bbd-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-424">Columns</span></span>  
  
-   <span data-ttu-id="e3bbd-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e3bbd-425">Procedures</span></span>  
  
-   <span data-ttu-id="e3bbd-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3bbd-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e3bbd-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3bbd-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e3bbd-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="e3bbd-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="e3bbd-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="e3bbd-429">Tables and Views</span></span>  
  
|<span data-ttu-id="e3bbd-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-430">ColumnName</span></span>|<span data-ttu-id="e3bbd-431">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-433">String</span></span>|  
|<span data-ttu-id="e3bbd-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-434">TABLE_OWNER</span></span>|<span data-ttu-id="e3bbd-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-435">String</span></span>|  
|<span data-ttu-id="e3bbd-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-436">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-437">String</span></span>|  
|<span data-ttu-id="e3bbd-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-438">TABLE_TYPE</span></span>|<span data-ttu-id="e3bbd-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-439">String</span></span>|  
|<span data-ttu-id="e3bbd-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-440">REMARKS</span></span>|<span data-ttu-id="e3bbd-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e3bbd-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="e3bbd-442">Columns</span></span>  
  
|<span data-ttu-id="e3bbd-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-443">ColumnName</span></span>|<span data-ttu-id="e3bbd-444">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-446">String</span></span>|  
|<span data-ttu-id="e3bbd-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-447">TABLE_OWNER</span></span>|<span data-ttu-id="e3bbd-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-448">String</span></span>|  
|<span data-ttu-id="e3bbd-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-449">TABLE_NAME</span></span>|<span data-ttu-id="e3bbd-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-450">String</span></span>|  
|<span data-ttu-id="e3bbd-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-451">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-452">String</span></span>|  
|<span data-ttu-id="e3bbd-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-453">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-454">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-454">Int16</span></span>|  
|<span data-ttu-id="e3bbd-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-455">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-456">String</span></span>|  
|<span data-ttu-id="e3bbd-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-457">PRECISION</span></span>|<span data-ttu-id="e3bbd-458">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-458">Int32</span></span>|  
|<span data-ttu-id="e3bbd-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-459">LENGTH</span></span>|<span data-ttu-id="e3bbd-460">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-460">Int32</span></span>|  
|<span data-ttu-id="e3bbd-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-461">SCALE</span></span>|<span data-ttu-id="e3bbd-462">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-462">Int16</span></span>|  
|<span data-ttu-id="e3bbd-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-463">RADIX</span></span>|<span data-ttu-id="e3bbd-464">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-464">Int16</span></span>|  
|<span data-ttu-id="e3bbd-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-465">NULLABLE</span></span>|<span data-ttu-id="e3bbd-466">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-466">Int16</span></span>|  
|<span data-ttu-id="e3bbd-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-467">REMARKS</span></span>|<span data-ttu-id="e3bbd-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-468">String</span></span>|  
|<span data-ttu-id="e3bbd-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-470">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e3bbd-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e3bbd-471">Procedures</span></span>  
  
|<span data-ttu-id="e3bbd-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-472">ColumnName</span></span>|<span data-ttu-id="e3bbd-473">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-475">String</span></span>|  
|<span data-ttu-id="e3bbd-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e3bbd-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-477">String</span></span>|  
|<span data-ttu-id="e3bbd-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-479">String</span></span>|  
|<span data-ttu-id="e3bbd-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e3bbd-481">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-481">Int16</span></span>|  
|<span data-ttu-id="e3bbd-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e3bbd-483">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-483">Int16</span></span>|  
|<span data-ttu-id="e3bbd-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e3bbd-485">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-485">Int16</span></span>|  
|<span data-ttu-id="e3bbd-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-486">REMARKS</span></span>|<span data-ttu-id="e3bbd-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-487">String</span></span>|  
|<span data-ttu-id="e3bbd-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e3bbd-489">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e3bbd-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3bbd-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e3bbd-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-491">ColumnName</span></span>|<span data-ttu-id="e3bbd-492">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e3bbd-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-494">String</span></span>|  
|<span data-ttu-id="e3bbd-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3bbd-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e3bbd-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-496">String</span></span>|  
|<span data-ttu-id="e3bbd-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-498">String</span></span>|  
|<span data-ttu-id="e3bbd-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-499">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-500">String</span></span>|  
|<span data-ttu-id="e3bbd-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-501">COLUMN_TYPE</span></span>|<span data-ttu-id="e3bbd-502">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-502">Int16</span></span>|  
|<span data-ttu-id="e3bbd-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-503">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-504">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-504">Int16</span></span>|  
|<span data-ttu-id="e3bbd-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-505">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-506">String</span></span>|  
|<span data-ttu-id="e3bbd-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-507">PRECISION</span></span>|<span data-ttu-id="e3bbd-508">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-508">Int32</span></span>|  
|<span data-ttu-id="e3bbd-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-509">LENGTH</span></span>|<span data-ttu-id="e3bbd-510">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-510">Int32</span></span>|  
|<span data-ttu-id="e3bbd-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e3bbd-511">SCALE</span></span>|<span data-ttu-id="e3bbd-512">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-512">Int16</span></span>|  
|<span data-ttu-id="e3bbd-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-513">RADIX</span></span>|<span data-ttu-id="e3bbd-514">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-514">Int16</span></span>|  
|<span data-ttu-id="e3bbd-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-515">NULLABLE</span></span>|<span data-ttu-id="e3bbd-516">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-516">Int16</span></span>|  
|<span data-ttu-id="e3bbd-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-517">REMARKS</span></span>|<span data-ttu-id="e3bbd-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-518">String</span></span>|  
|<span data-ttu-id="e3bbd-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="e3bbd-519">OVERLOAD</span></span>|<span data-ttu-id="e3bbd-520">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-520">Int32</span></span>|  
|<span data-ttu-id="e3bbd-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-522">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e3bbd-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3bbd-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e3bbd-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3bbd-524">ColumnName</span></span>|<span data-ttu-id="e3bbd-525">DataType</span><span class="sxs-lookup"><span data-stu-id="e3bbd-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3bbd-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e3bbd-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="e3bbd-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-527">String</span></span>|  
|<span data-ttu-id="e3bbd-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e3bbd-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e3bbd-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-529">String</span></span>|  
|<span data-ttu-id="e3bbd-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3bbd-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-531">String</span></span>|  
|<span data-ttu-id="e3bbd-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-532">COLUMN_NAME</span></span>|<span data-ttu-id="e3bbd-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-533">String</span></span>|  
|<span data-ttu-id="e3bbd-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-534">COLUMN_TYPE</span></span>|<span data-ttu-id="e3bbd-535">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-535">Int16</span></span>|  
|<span data-ttu-id="e3bbd-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-536">DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-537">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-537">Int16</span></span>|  
|<span data-ttu-id="e3bbd-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3bbd-538">TYPE_NAME</span></span>|<span data-ttu-id="e3bbd-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-539">String</span></span>|  
|<span data-ttu-id="e3bbd-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-540">COLUMN_SIZE</span></span>|<span data-ttu-id="e3bbd-541">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-541">Int32</span></span>|  
|<span data-ttu-id="e3bbd-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="e3bbd-543">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-543">Int32</span></span>|  
|<span data-ttu-id="e3bbd-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e3bbd-545">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-545">Int16</span></span>|  
|<span data-ttu-id="e3bbd-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e3bbd-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e3bbd-547">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-547">Int16</span></span>|  
|<span data-ttu-id="e3bbd-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e3bbd-548">NULLABLE</span></span>|<span data-ttu-id="e3bbd-549">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-549">Int16</span></span>|  
|<span data-ttu-id="e3bbd-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e3bbd-550">REMARKS</span></span>|<span data-ttu-id="e3bbd-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-551">String</span></span>|  
|<span data-ttu-id="e3bbd-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e3bbd-552">COLUMN_DEF</span></span>|<span data-ttu-id="e3bbd-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-553">String</span></span>|  
|<span data-ttu-id="e3bbd-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e3bbd-555">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-555">Int16</span></span>|  
|<span data-ttu-id="e3bbd-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e3bbd-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e3bbd-557">Int16</span><span class="sxs-lookup"><span data-stu-id="e3bbd-557">Int16</span></span>|  
|<span data-ttu-id="e3bbd-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3bbd-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e3bbd-559">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-559">Int32</span></span>|  
|<span data-ttu-id="e3bbd-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3bbd-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3bbd-561">Int32</span><span class="sxs-lookup"><span data-stu-id="e3bbd-561">Int32</span></span>|  
|<span data-ttu-id="e3bbd-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3bbd-562">IS_NULLABLE</span></span>|<span data-ttu-id="e3bbd-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e3bbd-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3bbd-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3bbd-564">See Also</span></span>  
 <span data-ttu-id="e3bbd-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e3bbd-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
