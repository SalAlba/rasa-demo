## Get started from website (including privacy clause etc)
* get_started_step3
    - action_greet_user

## Install Rasa: Happy Path
* install_rasa
    - utter_ask_python_installed
* mood_confirm
    - utter_ask_pip_or_conda
* enter_data{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* mood_confirm
    - utter_get_starter_pack
    - utter_direct_to_step4
    - utter_anything_else

## Install Rasa: Happy Path with already provided package_manager
* install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* mood_confirm
    - utter_get_starter_pack
    - utter_direct_to_step4
    - utter_anything_else 

## Install Rasa: No Python installed
* install_rasa
    - utter_ask_python_installed
* deny
    - utter_get_python
    - utter_ask_pip_or_conda
* enter_data{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build

## Install Rasa: Ask Python installed -> Which version
* install_rasa
    - utter_ask_python_installed
* ask_faq_python_version
    - action_faqs
    - utter_get_python
    - utter_ask_pip_or_conda
* enter_data{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build

## Install Rasa: Deny ready to build -> Ask if problem -> Yes
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* deny
    - utter_ask_if_problem
* mood_confirm
    - utter_ask_describe_problem
* technical_question OR enter_data OR out_of_scope
    - action_store_problem_description
    - utter_direct_to_forum_for_help

## Install Rasa: Deny ready to build -> Ask if problem -> technical question
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* deny
    - utter_ask_if_problem
* technical_question OR enter_data OR out_of_scope
    - action_store_problem_description
    - utter_direct_to_forum_for_help

## Install Rasa: Deny ready to build -> Ask if problem -> technical question
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* deny
    - utter_ask_if_problem
* deny
    - utter_anything_else

## Install Rasa: Ask ready to build -> Problem
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* technical_question OR enter_data OR out_of_scope
    - action_store_problem_description
    - utter_direct_to_forum_for_help
* mood_confirm OR thank
    - utter_anything_else


## Install Rasa: Ask ready to build -> FAQ
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* ask_faq_platform OR ask_faq_languages OR ask_faq_tutorialcore OR ask_faq_tutorialnlu OR ask_faq_opensource OR ask_faq_voice OR ask_faq_slots OR ask_faq_channels OR ask_faq_differencecorenlu
    - action_store_problem_description
    - action_faqs

## Install Rasa: Ask ready to build -> No -> FAQ
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* deny
    - utter_ask_if_problem
* ask_faq_platform OR ask_faq_languages OR ask_faq_tutorialcore OR ask_faq_tutorialnlu OR ask_faq_opensource OR ask_faq_voice OR ask_faq_slots OR ask_faq_channels OR ask_faq_differencecorenlu
    - action_store_problem_description
    - action_faqs


## Install Rasa: Ask ready to build -> No  -> Problem -> FAQ
* enter_data{"package_manager": "pip"} OR install_rasa{"package_manager": "pip"}
    - action_select_installation_command
    - utter_ask_ready_to_build
* deny
    - utter_ask_if_problem
* mood_confirm
    - utter_ask_describe_problem
* ask_faq_platform OR ask_faq_languages OR ask_faq_tutorialcore OR ask_faq_tutorialnlu OR ask_faq_opensource OR ask_faq_voice OR ask_faq_slots OR ask_faq_channels OR ask_faq_differencecorenlu
    - action_store_problem_description
    - action_faqs
