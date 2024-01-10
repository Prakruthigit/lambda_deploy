def config = [

  'dev': 'eu-west-3',

  'qa': 'eu-west-3',

  'uat': 'eu-west-3',

  'demo': 'eu-west-3',

  'acc': 'eu-west-3',

  'preprod': 'eu-west-3',

  'prod': 'eu-west-3',

  'dr': 'eu-central-1'

]
 
def ENV = [:]
 
for (env in config) {

  ENV[env] = [

    'onetmf-email-lambda': [

      tomail: 'ramakrishna.devalla@happiestminds.com',

      success: '${env} environment deployment is SUCCESS',

      failure: '${env} environment deployment is FAILURE',

      ecr_cred: "jenkins_ecr_${env}",

      region: config[env],

      func_name: "${env}-onetmf-email-lambda-${config[env].startsWith('eu-central') ? 'frankfurt' : 'paris'}",

      func_name_2: "${env}-notification-email-lambda-${config[env].startsWith('eu-central') ? 'frankfurt' : 'paris'}",

      func_name_3: "${env}-enate-communication-lambda-${config[env].startsWith('eu-central') ? 'frankfurt' : 'paris'}",

      jar_file: 'onetmf-email-lambda-0.0.1-aws'

    ]

  ]
  
  echo "${func_name}"

}





