# tides-integrated-system
Integration repo for deployed TiDES services

## Maintence
This repository will automatically update every 3 hours with changes to the submodules. If you need to update ahead of this schedule on your local clone then run the command:
```
git submodule update --remote --merge
```

## Development and Installation Instructions
### Development
This repository should rarely need developed directly into as it brings together the component submodules of the TiDES pipeline and marshal into one place for deployment, thus it only contains git submodule references to this and a docker-compose.yml which calls the submodule compose files and sets up the shared network resources. In the unlikely event that you do need to develop on it create a branch called ```[your-user]-dev``` and pull request this into ```dev``` to merge your changes.

### Installation
To install the ```tides-integrated-system``` you should need to follow the below instructions:

1. Git Clone this repository

2. ```cd tides-integrated-system```

3. ```docker compose up --build -d```

**Caveats**:

  You will need to have installed docker on the machine you are attempting to install on, you will also need to create a ```.env``` file that lives in the top level directory which will need to contain the necessary environment variable to connect to the remote database.

  You _do not_ need to git clone the induvidual submodules as these will be clones in with your initial clone command.
