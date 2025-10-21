# tides-integrated-system
Integration repo for deployed TiDES services

## Repository Description
There are two branches on the repository. ```main``` and ```dev```. ```main``` represents the production version and ```dev``` represents the development version. The submodules which are traced in in ```main``` call upon the production branches from each of the respective repo. In ```dev``` the submodules track the latest stable development branch. Because of the difference in the branches they are set to track there should be no need to ever merge these branches, unless changes to this README or the root ```docker-compose.yml``` takes place. In such a case ```dev``` should not be deleted.

## Maintence
This repository will automatically update every 3 hours with changes to the submodules. If you need to update ahead of this schedule on your local clone then run the command:
```
git submodule update --remote --merge
```

## Development and Installation Instructions
### Development
This repository should rarely need developed directly into as it brings together the component submodules of the TiDES pipeline and marshal into one place for deployment, thus it only contains git submodule references to this and a docker-compose.yml which calls the submodule compose files and sets up the shared network resources. You will however need to create a branch of this repository if you require the entire stack to operate during your own development. In order to do this, after creating any branches in the submodules:

1. Clone this repository
   
2. Create a branch called ```[your-user]-dev``` and swtich into it
   
3. Open ```.gitmodules``` and edit the branch name for the submodule(s) you are working on.
   
4. Run ```git submodule update --remote --merge```

If you are only editing submodules you should not merge this branch of this clone when you are done, only the branches of the submodules. If you have edited ```docker-compose.yml``` in this repository then you _should_ merge that change, but not the changes to ```.gitmodules```.

### Installation
To install the ```tides-integrated-system``` you should need to follow the below instructions:

1. Git Clone this repository

2. ```cd tides-integrated-system```

3. ```docker compose up --build -d```

**Caveats**:

  You will need to have installed docker on the machine you are attempting to install on, you will also need to create a ```.env``` file that lives in the top level directory which will need to contain the necessary environment variable to connect to the remote database.

  You _do not_ need to git clone the induvidual submodules as these will be clones in with your initial clone command.
