itk_module_test()

set(INPUTDATA ${CMAKE_CURRENT_SOURCE_DIR}/Data)
set(TEMP ${ITK_TEST_OUTPUT_DIR})

set(ITK_TEST_DRIVER itkTestDriver)

set(TextureFeaturesTests ScalarImageToRunLengthFeaturesImageFilterCreationTest.cxx
                         ScalarImageToRunLengthFeaturesImageFilterTest.cxx
                         ScalarImageToRunLengthFeaturesImageFilterTestSeparateFeatures.cxx
                         ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask.cxx
                         ScalarImageToRunLengthFeaturesImageFilterTestWithVectorImage.cxx
                         ScalarImageToRunLengthFeaturesImageFilterTestVectorImageSeparateFeatures.cxx
                         ScalarImageToTextureFeaturesImageFilterCreationTest.cxx
                         ScalarImageToTextureFeaturesImageFilterTest.cxx
                         ScalarImageToTextureFeaturesImageFilterTestSeparateFeatures.cxx
                         ScalarImageToTextureFeaturesImageFilterTestWithoutMask.cxx
                         ScalarImageToTextureFeaturesImageFilterTestWithVectorImage.cxx
                         ScalarImageToTextureFeaturesImageFilterTestVectorImageSeparateFeatures.cxx)

set(TestOutput ${ITK_TEST_OUTPUT_DIR})

CreateTestDriver(TextureFeatures "${TextureFeatures-Test_LIBRARIES}" "${TextureFeaturesTests}")

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterCreationTest
  COMMAND TextureFeaturesTestDriver
ScalarImageToRunLengthFeaturesImageFilterCreationTest)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask1
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultTestWithoutMask1.nrrd}
             ${TEMP}/resultTestWithoutMask1.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultTestWithoutMask1.nrrd
  10
  0 4200
  0 0.7
  2)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask2
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultTestWithoutMask2.nrrd}
             ${TEMP}/resultTestWithoutMask2.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultTestWithoutMask2.nrrd
  10
  0 4200
  0 1.25
  4)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask3
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultTestWithoutMask3.nrrd}
             ${TEMP}/resultTestWithoutMask3.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestWithoutMask
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultTestWithoutMask3.nrrd
  10
  0 4200
  0 1.8
  6)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterVectorlImage1
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultPartialImage1.nrrd}
             ${TEMP}/resultVectorImage1.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestWithVectorImage
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultVectorImage1.nrrd
  10
  0 4200
  0 0.7
  2)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterVectorImage2
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultPartialImage2.nrrd}
             ${TEMP}/resultVectorImage2.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestWithVectorImage
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultVectorImage2.nrrd
  10
  0 4200
  0 1.25
  4)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterPartialImage1
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultPartialImage1.nrrd}
             ${TEMP}/resultPartialImage1.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTest
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultPartialImage1.nrrd
  10
  0 4200
  0 0.7
  2)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterPartialImage2
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultPartialImage2.nrrd}
             ${TEMP}/resultPartialImage2.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTest
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultPartialImage2.nrrd
  10
  0 4200
  0 1.25
  4)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterTestWholeImage
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultWholeImage.nrrd}
             ${TEMP}/resultWholeImage.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTest
  DATA{${INPUTDATA}/Scan_CBCT_13R.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R.nrrd}
  ${TEMP}/resultWholeImage.nrrd
  10
  0 4200
  0 0.7
  2)

itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterTestSeparateFeatures
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_1.nrrd}
             ${TEMP}/resultSeparateFeatures_1.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_2.nrrd}
             ${TEMP}/resultSeparateFeatures_2.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_3.nrrd}
             ${TEMP}/resultSeparateFeatures_3.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_4.nrrd}
             ${TEMP}/resultSeparateFeatures_4.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_5.nrrd}
             ${TEMP}/resultSeparateFeatures_5.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_6.nrrd}
             ${TEMP}/resultSeparateFeatures_6.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_7.nrrd}
             ${TEMP}/resultSeparateFeatures_7.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_8.nrrd}
             ${TEMP}/resultSeparateFeatures_8.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_9.nrrd}
             ${TEMP}/resultSeparateFeatures_9.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_0.nrrd}
             ${TEMP}/resultSeparateFeatures_0.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestSeparateFeatures
  DATA{${INPUTDATA}/Scan_CBCT_13R.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R.nrrd}
  ${TEMP}/resultSeparateFeatures
  10
  0 4200
  0 1.25
  4)


itk_add_test(NAME ScalarImageToRunLengthFeaturesImageFilterTestVectorImageSeparateFeatures
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_1.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_1.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_2.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_2.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_3.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_3.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_4.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_4.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_5.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_5.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_6.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_6.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_7.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_7.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_8.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_8.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_9.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_9.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_0.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_0.nrrd
  ScalarImageToRunLengthFeaturesImageFilterTestVectorImageSeparateFeatures
  DATA{${INPUTDATA}/Scan_CBCT_13R.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R.nrrd}
  ${TEMP}/resultVectorImageSeparateFeatures
  10
  0 4200
  0 1.25
  4)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterCreationTest
  COMMAND TextureFeaturesTestDriver
ScalarImageToTextureFeaturesImageFilterCreationTest)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterTestWithoutMask1
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultTestWithoutMask4.nrrd}
             ${TEMP}/resultTestWithoutMask4.nrrd
  ScalarImageToTextureFeaturesImageFilterTestWithoutMask
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultTestWithoutMask4.nrrd
  10
  0 4200
  2)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterTestWithoutMask2
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultTestWithoutMask5.nrrd}
             ${TEMP}/resultTestWithoutMask5.nrrd
  ScalarImageToTextureFeaturesImageFilterTestWithoutMask
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultTestWithoutMask5.nrrd
  10
  0 4200
  4)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterTestWithoutMask3
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultTestWithoutMask6.nrrd}
             ${TEMP}/resultTestWithoutMask6.nrrd
  ScalarImageToTextureFeaturesImageFilterTestWithoutMask
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultTestWithoutMask6.nrrd
  10
  0 4200
  6)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterVectorlImage1
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultPartialImage3.nrrd}
             ${TEMP}/resultVectorImage3.nrrd
  ScalarImageToTextureFeaturesImageFilterTestWithVectorImage
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultVectorImage3.nrrd
  10
  0 4200
  2)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterVectorImage2
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultPartialImage4.nrrd}
             ${TEMP}/resultVectorImage4.nrrd
  ScalarImageToTextureFeaturesImageFilterTestWithVectorImage
  DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
  ${TEMP}/resultVectorImage4.nrrd
  10
  0 4200
  4)


itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterPartialImage1
COMMAND TextureFeaturesTestDriver
--compare  DATA{${INPUTDATA}/resultPartialImage3.nrrd}
           ${TEMP}/resultPartialImage3.nrrd
ScalarImageToTextureFeaturesImageFilterTest
DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
${TEMP}/resultPartialImage3.nrrd
10
0 4200
2)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterPartialImage2
COMMAND TextureFeaturesTestDriver
--compare  DATA{${INPUTDATA}/resultPartialImage4.nrrd}
           ${TEMP}/resultPartialImage4.nrrd
ScalarImageToTextureFeaturesImageFilterTest
DATA{${INPUTDATA}/Scan_CBCT_13R_D1_crop.nrrd}
DATA{${INPUTDATA}/SegmC_CBCT_13R_D1_crop.nrrd}
${TEMP}/resultPartialImage4.nrrd
10
0 4200
4)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterTestWholeImage
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultWholeImage2.nrrd}
             ${TEMP}/resultWholeImage2.nrrd
  ScalarImageToTextureFeaturesImageFilterTest
  DATA{${INPUTDATA}/Scan_CBCT_13R.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R.nrrd}
  ${TEMP}/resultWholeImage2.nrrd
  10
  0 4200
  2)

itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterTestSeparateFeatures
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_11.nrrd}
             ${TEMP}/resultSeparateFeatures_11.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_12.nrrd}
             ${TEMP}/resultSeparateFeatures_12.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_13.nrrd}
             ${TEMP}/resultSeparateFeatures_13.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_14.nrrd}
             ${TEMP}/resultSeparateFeatures_14.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_15.nrrd}
             ${TEMP}/resultSeparateFeatures_15.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_16.nrrd}
             ${TEMP}/resultSeparateFeatures_16.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_17.nrrd}
             ${TEMP}/resultSeparateFeatures_17.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_18.nrrd}
             ${TEMP}/resultSeparateFeatures_18.nrrd
  ScalarImageToTextureFeaturesImageFilterTestSeparateFeatures
  DATA{${INPUTDATA}/Scan_CBCT_13R.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R.nrrd}
  ${TEMP}/resultSeparateFeatures
  10
  0 4200
  4)


itk_add_test(NAME ScalarImageToTextureFeaturesImageFilterTestVectorImageSeparateFeatures
  COMMAND TextureFeaturesTestDriver
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_11.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_11.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_12.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_12.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_13.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_13.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_14.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_14.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_15.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_15.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_16.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_16.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_17.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_17.nrrd
  --compare  DATA{${INPUTDATA}/resultSeparateFeatures_18.nrrd}
             ${TEMP}/resultVectorImageSeparateFeatures_18.nrrd
  ScalarImageToTextureFeaturesImageFilterTestVectorImageSeparateFeatures
  DATA{${INPUTDATA}/Scan_CBCT_13R.nrrd}
  DATA{${INPUTDATA}/SegmC_CBCT_13R.nrrd}
  ${TEMP}/resultVectorImageSeparateFeatures
  10
  0 4200
  4)
