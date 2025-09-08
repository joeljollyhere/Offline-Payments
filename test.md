# Changes That Was Made For The N400Premium Product
## Application.xml
* Addition of new pages (13.1.1, 13.3)
* Moved last 3 sections from 13.1 to 13.1.1
   * How many people in your household, including yourself, are earning income?
   * Are you the head of the household?
   * What is the name of the head of the household?
   * Removed unused show/hide js code.
* Added new sections to 13.1.1
   * Are you currently married and did you and your spouse file a joint federal income tax return?
   * Is anyone else in your household (not a dependent) contributing income that has not already been included in the total household income you entered?
   * Added Js code for show hide
   * Repeater - Please provide details of other household contributors:
     * Name of contributing household member
     * Annual income of this person
     * Household size for this person (if separate household)
* Added 2 images for reference to the user (1040 & 1040-SR) in 13.1.2
* 13.2 changed from StopPage to AttentionPage
* 13.2 New attentionPage

## ResourceBundle.properties - Key updates
* immigrationreviewerreview_useremail-text3,SQ-10.2.pagetext.16,SQ-10.2.pagetext.16.personalisation,SQ-13.1.pageheader,SQ-13.1.page.title,SQ-13.1.label1,SQ-13.1.label1.instruction,SQ-13.1.label2,SQ-13.1.label2.instruction,SQ-13.1.label3.instruction
  SQ-13.1.label4.instruction,SQ-13.1.label5,SQ-13.1.label5.instruction,SQ-13.1.1.repeater.error,SQ-13.2.contentHeading,SQ-13.2.label,SQ-13.2.label.personalisation,SQ-13.2.stopPageText,SQ-13.2.stopPageText.personalisation,SQ-13.3.pageheader.hide
  SQ-13.3.page.title,SQ-13.3.stopPageText,SQ-13.3.stopPageText.personalisation,SQ-13.3.label,SQ-13.1.1.pageheader,SQ-13.1.1.page.title,SQ-13.1.1.label1,SQ-13.1.1.label1.1,SQ-13.1.1.label1.2,SQ-13.1.1.label2
  SQ-13.1.1.label2.instruction,contributor.count,contributor.addAnotherKey,SQ-13.1.1.label3,SQ-13.1.1.label4,SQ-13.1.1.label5,SQ-13.1.1.label6,SQ-13.1.1.pagetext.1,SQ-13.1.1.label7,SQ-13.1.1.label8
  SQ-13.1.1.label9,other_contributor_review,other_contributor_counts,SQ-13.1.1.label10,SQ-13.1.1.label11,SQ-13.1.1.label12,householdsize.row1,householdsize.row2,householdsize.row3,householdsize.row4
  householdsize.row5,householdsize.row6,householdsize.row7,householdsize.row8,householdsize.row9,householdsize.row10,householdsize.row11,householdsize.row12,householdsize.row13,householdsize.row14
  householdsize.row15,householdsize.row16,householdsize.row17,householdsize.row18,householdsize.row19,householdsize.row20,SQ-13.1.2.page.title,SQ-13.1.2.pageheader,federaltaxreturn.example,federaltaxreturn.instruction.1,federaltaxreturn.instruction.2,Form1040.imagepath,Form1040SR.imagepath,SQ-13.1.2.label1,SQ-13.1.2.label1.instruction,SQ-13.1.2.label2,SQ-13.1.2.label2.instruction,SQ-13.1.2.label3

## ObjectScrubber.java - Mapping updates
* To handle mapping in 13.1.1 - hasMultipleIncomeContributors and householdSizeIncludingContributors
* To handle mapping in 13.2 - noReducedFeeOptionDueToIncomeSources
* To handle mapping in 13.3 - noReducedFeeOptionDueToLackOfDocumentation

## Applicant.java, Contributors.java, FeeReduction.kt, FormSpecific.java - To add new attributes
* Applicant.java
  * youProvidedFinancialSupport
* Contributors.java
  * contributingHouseholdMember,annualIncomeOfTheContributingMember,householdSizeOfTheContributingMember
* FeeReduction.kt
  * filedIncomeTaxReturn, provideIncomeTaxReturn, recentPayStubs, notEligibleForReducedFee, cannotProvideDocumentation, anyOtherContributors, areYouCurrentlyMarried
      * FormSpecific.java
        * contributors, contributorsCount

## N400premium.java - For show/hide, Flow conditions, Condition Updates
* Flow Conditions
  * isUserhavingIncomeDocument, isUserHavingIncomeSources,
* Show/Hide
  * isEligibleForUSCitizenship, isHavingMoreContributors,
* getYouProvidedFinancialSupport
  * Dynamic copy for 10.2 question
* Helpers
  * getEligibliityForUSCitizenship, getTotalHouseholdMembers, getIncomeDocumentAvailability, isEligibleForFeeReduction, getTotalIncome, getTotalHousehold
	
## src/main/webapp/appImages/ - Addition of new images as an example for the user in the SQ.
* Added 2 images - Form1040.png and Form1040SR.png

## Checkbok.tag - Existing tag

## Children.tag - Property update
* enabled personalisation and added prProperty="youProvidedFinancialSupport" for currentlyProvideFinancialSupport

## Contributors.tag - New tag that was added by me
* new tag with these new properties contributingHouseholdMember, annualIncomeOfTheContributingMember and householdSizeOfTheContributingMember
## DDM_Numbers.tag - Tag update.
* Added support for repeater validation `controlInsideRepeater`
 
## n400premium-rules-drools.xls - For the page navigation based on condition.

## pagetemplate.vm - To support the new pages SQ-13.2,SQ-13.3


